# TsgcWebSocketServer_HTTPAPI - Example

Full source of `uServerChat.pas` from the **03.WebSocket_High_Performance_Server/01.HTTP_SYS_WebSocket_Server** demo, which uses `TsgcWebSocketServer_HTTPAPI`.

API reference: [TsgcWebSocketServer_HTTPAPI](../reference/api/TsgcWebSocketServer_HTTPAPI.md)
Source demo: `03.WebSocket_High_Performance_Server/01.HTTP_SYS_WebSocket_Server` (file `uServerChat.pas`)

```pascal
unit uServerChat;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, sgcWebSocket_Classes, sgcWebSocket, sgcWebSocket_Const,
  StdCtrls, ExtCtrls, sgcWebSocket_Classes_Indy, sgcWebSocket_Server_Base,
  sgcWebSocket_Server_HTTPAPI, idsync, sgcBase_Classes, sgcTCP_Classes,
  sgcHTTP_Classes, sgcHTTP_OAuth_Server, sgcHTTP_OAuth2_Server, sgcHTTP,
  sgcWebSocket_Classes_HTTPAPI, sgcWebSocket_HTTPAPI, sgcSocket_Classes;

type
  TfrmHTTPAPIServerChat = class(TForm)
    pnlServer: TPanel;
    btnStop: TButton;
    btnStart: TButton;
    memoLog: TMemo;
    pnlServerActive: TPanel;
    pnlServerOptions: TPanel;
    Label1: TLabel;
    txtHost: TEdit;
    Label2: TLabel;
    txtDefaultPort: TEdit;
    Label3: TLabel;
    Default: TLabel;
    chkAuthentication: TCheckBox;
    txtAuthUser: TEdit;
    txtAuthPassword: TEdit;
    Label6: TLabel;
    WSServer: TsgcWebSocketServer_HTTPAPI;
    chkSSL: TCheckBox;
    txtHash: TEdit;
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure chkAuthenticationClick(Sender: TObject);
    procedure OAuth2OAuth2Authentication(Connection: TsgcWSConnection;
      OAuth2: TsgcHTTPOAuth2Request; aUser, aPassword: string;
      var Authenticated: Boolean);
    procedure OAuth2OAuth2BeforeRequest(Sender: TObject;
      aConnection: TsgcWSConnection; aHeaders: TStringList;
      var Cancel: Boolean);
    procedure WSServerAuthentication(Connection: TsgcWSConnection;
      aUser, aPassword: string; var Authenticated: Boolean);
    procedure WSServerConnect(Connection: TsgcWSConnection);
    procedure WSServerError(Connection: TsgcWSConnection; const Error: string);
    procedure WSServerMessage(Connection: TsgcWSConnection; const Text: string);
    procedure WSServerDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSServerHTTPRequest(aConnection: TsgcWSConnection_HTTPAPI; const
        aRequestInfo: THttpServerRequest; var aResponseInfo: THttpServerResponse);
    procedure WSServerStartup(Sender: TObject);
  private
    procedure DoConnect;
  end;

var
  frmHTTPAPIServerChat: TfrmHTTPAPIServerChat;

implementation

uses
  Registry;

{$R *.dfm}

function sgcIsAdmin: Boolean;
var
  oRegistry: TRegistry;
begin
  oRegistry := TRegistry.Create(KEY_READ);
  Try
    oRegistry.RootKey := HKEY_LOCAL_MACHINE;
    oRegistry.Access := KEY_WRITE;
    result := oRegistry.OpenKey('Software\eSeGeCe\sgcWebsockets\', True);
    oRegistry.CloseKey;
  Finally
    oRegistry.Free;
  End;
end;

procedure TfrmHTTPAPIServerChat.FormCreate(Sender: TObject);
begin


  btnStart.Click;
end;

procedure TfrmHTTPAPIServerChat.btnStartClick(Sender: TObject);
begin
  // ... bindings
  WSServer.Host := txtHost.Text;
  WSServer.Port := StrToInt(txtDefaultPort.Text);

  // ... authentication
  if chkAuthentication.Checked then
    WSServer.Authentication.AuthUsers.Add(txtAuthUser.Text + '=' +
      txtAuthPassword.Text);

  // ... ssl
  WSServer.SSL := chkSSL.Checked;
  if WSServer.SSL then
    WSServer.SSLOptions.Hash := txtHash.Text;

  // ... active
  WSServer.Active := True;
end;

procedure TfrmHTTPAPIServerChat.btnStopClick(Sender: TObject);
begin
  WSServer.Active := False;

  if not WSServer.Active then
  begin
    memoLog.Lines.Add('#Server Stopped');
    pnlServerOptions.Enabled := True;
  end;
end;

procedure TfrmHTTPAPIServerChat.chkAuthenticationClick(Sender: TObject);
begin
  WSServer.Authentication.Enabled := chkAuthentication.Checked;
end;

procedure TfrmHTTPAPIServerChat.DoConnect;
begin
  memoLog.Lines.Add('#Server Started: ' + txtHost.Text + ':' +
    txtDefaultPort.Text);
  if chkAuthentication.Checked then
    memoLog.Lines.Add('#Authentication Enabled');
  if chkSSL.Checked then
    memoLog.Lines.Add('#SSL Enabled');
  pnlServerOptions.Enabled := False;
end;

procedure TfrmHTTPAPIServerChat.OAuth2OAuth2Authentication
  (Connection: TsgcWSConnection; OAuth2: TsgcHTTPOAuth2Request;
  aUser, aPassword: string; var Authenticated: Boolean);
begin
  if ((aUser = txtAuthUser.Text) and (aPassword = txtAuthPassword.Text)) then
    Authenticated := True;
end;

procedure TfrmHTTPAPIServerChat.OAuth2OAuth2BeforeRequest(Sender: TObject;
  aConnection: TsgcWSConnection; aHeaders: TStringList; var Cancel: Boolean);
begin
  ShowMessage(aHeaders.Text);
end;

procedure TfrmHTTPAPIServerChat.WSServerAuthentication
  (Connection: TsgcWSConnection; aUser, aPassword: string;
  var Authenticated: Boolean);
begin
  Authenticated := (aUser = txtAuthUser.Text) and (aPassword = txtAuthPassword.Text);
  TThread.Queue(nil,
    procedure
    begin
      memoLog.Lines.Add('#Authentication: ' + aUser + ':' + aPassword);
    end);
end;

procedure TfrmHTTPAPIServerChat.WSServerConnect(Connection: TsgcWSConnection);
begin
  TThread.Queue(nil,
    procedure
    begin
      memoLog.Lines.Add('Connected: ' + Connection.IP);
    end);
end;

procedure TfrmHTTPAPIServerChat.WSServerDisconnect(Connection: TsgcWSConnection;
Code: Integer);
begin
  TThread.Queue(nil,
    procedure
    begin
      memoLog.Lines.Add('Disconnected (' + IntToStr(Code) + '): ' +
        Connection.IP);
    end);
end;

procedure TfrmHTTPAPIServerChat.WSServerError(Connection: TsgcWSConnection;
const Error: string);
begin
  TThread.Queue(nil,
    procedure
    begin
      memoLog.Lines.Add('Error: ' + Connection.IP + ' - ' + Error);
    end);
end;

procedure TfrmHTTPAPIServerChat.WSServerHTTPRequest(aConnection:
    TsgcWSConnection_HTTPAPI; const aRequestInfo: THttpServerRequest; var
    aResponseInfo: THttpServerResponse);
begin
  aResponseInfo.ResponseNo := 200;
end;

procedure TfrmHTTPAPIServerChat.WSServerMessage(Connection: TsgcWSConnection;
const Text: string);
begin
  TThread.Queue(nil,
    procedure
    begin
      memoLog.Lines.Add(Connection.IP + ':' + Text);
      WSServer.Broadcast(Text);
    end);
end;

procedure TfrmHTTPAPIServerChat.WSServerStartup(Sender: TObject);
begin
  idsync.TIdNotify.NotifyMethod(DoConnect);
end;

end.
```

