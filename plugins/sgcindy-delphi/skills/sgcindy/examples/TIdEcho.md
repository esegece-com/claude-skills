# TIdEcho - Example

Full source of `fEchoClient.pas` from the **EchoClient** demo, which uses `TIdEcho`.

API reference: [TIdEcho](../reference/api/TIdEcho.md)
Source demo: `EchoClient` (file `fEchoClient.pas`)

```pascal
{ ***************************************************************************
  sgcIndy Echo Client Demo

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit fEchoClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls,
  IdBaseComponent, IdComponent, IdTCPConnection, IdTCPClient, IdEcho;

type
  TfrmEchoClient = class(TForm)
    lblHost: TLabel;
    txtHost: TEdit;
    lblPort: TLabel;
    txtPort: TEdit;
    lblMessage: TLabel;
    txtMessage: TEdit;
    btnEcho: TButton;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnEchoClick(Sender: TObject);
  private
    fEchoClient: TIdEcho;
    procedure DoLog(const aText: string);
  public
  end;

var
  frmEchoClient: TfrmEchoClient;

implementation

{$R *.dfm}

procedure TfrmEchoClient.FormCreate(Sender: TObject);
begin
  fEchoClient := TIdEcho.Create(nil);
end;

procedure TfrmEchoClient.FormDestroy(Sender: TObject);
begin
  if fEchoClient.Connected then
    fEchoClient.Disconnect;
  FreeAndNil(fEchoClient);
end;

procedure TfrmEchoClient.DoLog(const aText: string);
begin
  memoLog.Lines.Add(aText);
end;

procedure TfrmEchoClient.btnEchoClick(Sender: TObject);
var
  vReply: string;
begin
  memoLog.Lines.Clear;
  fEchoClient.Host := txtHost.Text;
  fEchoClient.Port := StrToIntDef(txtPort.Text, 7);
  try
    fEchoClient.Connect;
    DoLog('Connected to ' + fEchoClient.Host + ':' +
      IntToStr(fEchoClient.Port));
    vReply := fEchoClient.Echo(txtMessage.Text);
    DoLog('Sent: ' + txtMessage.Text);
    DoLog('Received: ' + vReply);
    fEchoClient.Disconnect;
    DoLog('Disconnected');
  except
    on E: Exception do
      DoLog('Error: ' + E.Message);
  end;
end;

end.
```

