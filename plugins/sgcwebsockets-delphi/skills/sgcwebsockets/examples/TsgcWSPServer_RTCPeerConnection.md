# TsgcWSPServer_RTCPeerConnection - Example

Full source of `FRTC_WebSocketServer.pas` from the **35.P2P/05.RTCPeerConnection** demo, which uses `TsgcWSPServer_RTCPeerConnection`.

API reference: [TsgcWSPServer_RTCPeerConnection](../reference/api/TsgcWSPServer_RTCPeerConnection.md)
Source demo: `35.P2P/05.RTCPeerConnection` (file `FRTC_WebSocketServer.pas`)

```pascal
unit FRTC_WebSocketServer;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, DB, Grids, DBGrids, DBClient, Math, Activex,
  StrUtils,
  // sgc
  sgcWebSocket_Server, sgcWebSocket,  sgcWebSocket_Classes, sgcBase_Classes,
  sgcTCP_Classes, sgcWebSocket_Classes_Indy, sgcSocket_Classes,
  sgcWebSocket_Types, sgcWebSocket_Protocol_Base_Server,
  sgcWebSocket_Protocol_RTCPeerConnection_Server, sgcWebSocket_Protocols;

type
  TfrmServer = class(TForm)
    btnStart: TButton;
    btnStop: TButton;
    WSServer: TsgcWebSocketServer;
    pnlServer: TPanel;
    memoLog: TMemo;
    sgcWSPServer_RTCPeerConnection1: TsgcWSPServer_RTCPeerConnection;
    txtIPAddress: TEdit;
    Label1: TLabel;
    Label2: TLabel;
    txtPort: TEdit;
    chkSSL: TCheckBox;
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure sgcWSPServer_RTCPeerConnection1Connect(Connection: TsgcWSConnection);
    procedure sgcWSPServer_RTCPeerConnection1Disconnect(Connection:
        TsgcWSConnection; Code: Integer);
    procedure sgcWSPServer_RTCPeerConnection1Error(Connection: TsgcWSConnection;
        const Error: string);
  private
    procedure DoLog(const aText: String);
  end;

var
  frmServer: TfrmServer;

implementation


{$R *.dfm}

procedure TfrmServer.FormCreate(Sender: TObject);
begin
  btnStart.Click;
end;

procedure TfrmServer.btnStartClick(Sender: TObject);
begin
  if not WSServer.Active then
  begin
    With WSServer.Bindings.Add do
    begin
      IP := txtIPAddress.text;
      Port := StrToInt(txtPort.Text);
    end;
    WSServer.Port := StrToInt(txtPort.Text);
    WSServer.SSLOptions.Port := WSServer.Port;
    WSServer.SSLOptions.CertFile := 'sgc.pem';
    WSServer.SSLOptions.KeyFile := 'sgc.pem';
    WSServer.SSL := chkSSL.Checked;

    WSServer.Active := True;
    DoLog('#started');
  end;
end;

procedure TfrmServer.btnStopClick(Sender: TObject);
begin
  if WSServer.Active then
  begin
    WSServer.Active := False;
    WSServer.Bindings.Clear;
    DoLog('#stopped');
  end;
end;

procedure TfrmServer.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
end;

procedure TfrmServer.sgcWSPServer_RTCPeerConnection1Connect(Connection:
    TsgcWSConnection);
begin
  memoLog.Lines.Add('Connected: ' + Connection.Guid);
end;

procedure TfrmServer.sgcWSPServer_RTCPeerConnection1Disconnect(Connection:
    TsgcWSConnection; Code: Integer);
begin
  memoLog.Lines.Add('Disconnected (' + IntToStr(Code) + '): ' + Connection.Guid);
end;

procedure TfrmServer.sgcWSPServer_RTCPeerConnection1Error(Connection:
    TsgcWSConnection; const Error: string);
begin
  memoLog.Lines.Add('Error: ' + Connection.Guid + ':' + Error);
end;

end.
```

