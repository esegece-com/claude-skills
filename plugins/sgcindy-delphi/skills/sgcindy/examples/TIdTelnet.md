# TIdTelnet - Example

Full source of `fTelnetClient.pas` from the **TelnetClient** demo, which uses `TIdTelnet`.

API reference: [TIdTelnet](../reference/api/TIdTelnet.md)
Source demo: `TelnetClient` (file `fTelnetClient.pas`)

```pascal
{ ***************************************************************************
  sgcIndy Telnet Client Demo

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit fTelnetClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls,
  IdBaseComponent, IdComponent, IdTCPConnection, IdTCPClient, IdTelnet;

type
  TfrmTelnetClient = class(TForm)
    lblHost: TLabel;
    lblPort: TLabel;
    lblCommand: TLabel;
    txtHost: TEdit;
    txtPort: TEdit;
    btnConnect: TButton;
    btnDisconnect: TButton;
    txtCommand: TEdit;
    btnSend: TButton;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnConnectClick(Sender: TObject);
    procedure btnDisconnectClick(Sender: TObject);
    procedure btnSendClick(Sender: TObject);
  private
    FTelnet: TIdTelnet;
    procedure OnDataAvailable(Sender: TIdTelnet; const Buffer: String);
    procedure DoLog(const aText: String);
  public
  end;

var
  frmTelnetClient: TfrmTelnetClient;

implementation

{$R *.dfm}

procedure TfrmTelnetClient.FormCreate(Sender: TObject);
begin
  FTelnet := TIdTelnet.Create(nil);
  FTelnet.OnDataAvailable := OnDataAvailable;
end;

procedure TfrmTelnetClient.FormDestroy(Sender: TObject);
begin
  FTelnet.Free;
end;

procedure TfrmTelnetClient.btnConnectClick(Sender: TObject);
begin
  FTelnet.Host := txtHost.Text;
  FTelnet.Port := StrToInt(txtPort.Text);
  FTelnet.Connect;
  DoLog('Connected to ' + txtHost.Text + ':' + txtPort.Text);
end;

procedure TfrmTelnetClient.btnDisconnectClick(Sender: TObject);
begin
  FTelnet.Disconnect;
  DoLog('Disconnected.');
end;

procedure TfrmTelnetClient.btnSendClick(Sender: TObject);
begin
  FTelnet.SendCh(txtCommand.Text + #13#10);
end;

procedure TfrmTelnetClient.OnDataAvailable(Sender: TIdTelnet;
  const Buffer: String);
begin
  DoLog(Buffer);
end;

procedure TfrmTelnetClient.DoLog(const aText: String);
begin
  TThread.Queue(nil, procedure
    begin
      memoLog.Lines.Add(aText);
    end);
end;

end.
```

