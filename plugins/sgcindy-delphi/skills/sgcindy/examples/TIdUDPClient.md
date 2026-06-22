# TIdUDPClient - Example

Full source of `fUDPClientServer.pas` from the **UDPClientServer** demo, which uses `TIdUDPClient`.

API reference: [TIdUDPClient](../reference/api/TIdUDPClient.md)
Source demo: `UDPClientServer` (file `fUDPClientServer.pas`)

```pascal
{ ***************************************************************************
  sgcIndy UDP Client/Server Demo

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit fUDPClientServer;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls,
  IdBaseComponent, IdComponent, IdUDPBase, IdUDPClient, IdUDPServer,
  IdGlobal, IdSocketHandle;

type
  TfrmUDPClientServer = class(TForm)
    grpServer: TGroupBox;
    lblServerPort: TLabel;
    txtServerPort: TEdit;
    btnStartServer: TButton;
    btnStopServer: TButton;
    grpClient: TGroupBox;
    lblTargetHost: TLabel;
    lblTargetPort: TLabel;
    lblMessage: TLabel;
    txtTargetHost: TEdit;
    txtTargetPort: TEdit;
    txtMessage: TEdit;
    btnSend: TButton;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnStartServerClick(Sender: TObject);
    procedure btnStopServerClick(Sender: TObject);
    procedure btnSendClick(Sender: TObject);
  private
    FUDPServer: TIdUDPServer;
    FUDPClient: TIdUDPClient;
    procedure OnUDPRead(AThread: TIdUDPListenerThread; const AData: TIdBytes;
      ABinding: TIdSocketHandle);
    procedure DoLog(const AText: string);
  public
  end;

var
  frmUDPClientServer: TfrmUDPClientServer;

implementation

{$R *.dfm}

procedure TfrmUDPClientServer.FormCreate(Sender: TObject);
begin
  FUDPServer := TIdUDPServer.Create(nil);
  FUDPServer.OnUDPRead := OnUDPRead;

  FUDPClient := TIdUDPClient.Create(nil);
end;

procedure TfrmUDPClientServer.FormDestroy(Sender: TObject);
begin
  FUDPClient.Free;
  FUDPServer.Active := False;
  FUDPServer.Free;
end;

procedure TfrmUDPClientServer.btnStartServerClick(Sender: TObject);
begin
  try
    FUDPServer.DefaultPort := StrToInt(txtServerPort.Text);
    FUDPServer.Active := True;
    DoLog('Server started on port ' + txtServerPort.Text);
  except
    on E: Exception do
      DoLog('Error starting server: ' + E.Message);
  end;
end;

procedure TfrmUDPClientServer.btnStopServerClick(Sender: TObject);
begin
  try
    FUDPServer.Active := False;
    DoLog('Server stopped');
  except
    on E: Exception do
      DoLog('Error stopping server: ' + E.Message);
  end;
end;

procedure TfrmUDPClientServer.btnSendClick(Sender: TObject);
begin
  try
    FUDPClient.Host := txtTargetHost.Text;
    FUDPClient.Port := StrToInt(txtTargetPort.Text);
    FUDPClient.Send(txtMessage.Text);
    DoLog('Sent to ' + txtTargetHost.Text + ':' + txtTargetPort.Text + ' -> ' +
      txtMessage.Text);
  except
    on E: Exception do
      DoLog('Error sending: ' + E.Message);
  end;
end;

procedure TfrmUDPClientServer.OnUDPRead(AThread: TIdUDPListenerThread;
  const AData: TIdBytes; ABinding: TIdSocketHandle);
var
  vText: string;
begin
  vText := BytesToString(AData);
  TThread.Queue(nil, procedure
    begin
      DoLog('Received from ' + ABinding.PeerIP + ':' +
        IntToStr(ABinding.PeerPort) + ' -> ' + vText);
    end);
end;

procedure TfrmUDPClientServer.DoLog(const AText: string);
begin
  TThread.Queue(nil, procedure
    begin
      memoLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) + ' ' + AText);
    end);
end;

end.
```

