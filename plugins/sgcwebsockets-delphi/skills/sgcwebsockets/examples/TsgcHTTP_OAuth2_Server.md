# TsgcHTTP_OAuth2_Server - Example

Full source of `FOAuth2_Server.pas` from the **20.HTTP_Protocol/02.OAuth2_Authentication** demo, which uses `TsgcHTTP_OAuth2_Server`.

API reference: [TsgcHTTP_OAuth2_Server](../reference/api/TsgcHTTP_OAuth2_Server.md)
Source demo: `20.HTTP_Protocol/02.OAuth2_Authentication` (file `FOAuth2_Server.pas`)

```pascal
unit FOAuth2_Server;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, sgcHTTP_Classes, sgcHTTP_OAuth_Server, sgcHTTP_OAuth2_Server,
  sgcHTTP, sgcBase_Classes, sgcTCP_Classes, sgcWebSocket_Classes,
  sgcWebSocket_Classes_Indy, sgcWebSocket_Server, sgcWebSocket, StdCtrls,
  ExtCtrls,
  // indy
  IdContext, IdCustomHTTPServer, sgcSocket_Classes;

type
  TFRMOAuth2Server = class(TForm)
    pnlServerActive: TPanel;
    btnStart: TButton;
    btnStop: TButton;
    pnlServerOptions: TPanel;
    Label1: TLabel;
    Label2: TLabel;
    Label3: TLabel;
    Default: TLabel;
    txtHost: TEdit;
    txtDefaultPort: TEdit;
    memoLog: TMemo;
    GroupBox1: TGroupBox;
    Label4: TLabel;
    Label5: TLabel;
    Label6: TLabel;
    Label7: TLabel;
    txtRedirectURI: TEdit;
    txtClientId: TEdit;
    txtClientSecret: TEdit;
    txtAppName: TEdit;
    chkOAuth2: TCheckBox;
    WSServer: TsgcWebSocketHTTPServer;
    OAuth2: TsgcHTTP_OAuth2_Server;
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure OAuth2OAuth2AfterAccessToken(Sender: TObject;
      Connection: TsgcWSConnection; OAuth2: TsgcHTTPOAuth2Request;
      aResponse: string);
    procedure OAuth2OAuth2AfterValidateAccessToken(Sender: TObject;
      Connection: TsgcWSConnection; OAuth2: TsgcHTTPOAuth2Request;
      var IsValid: Boolean);
    procedure OAuth2OAuth2Authentication(Connection: TsgcWSConnection;
      OAuth2: TsgcHTTPOAuth2Request; aUser, aPassword: string;
      var Authenticated: Boolean);
    procedure WSServerCommandGet(AContext: TIdContext;
      ARequestInfo: TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
    procedure WSServerConnect(Connection: TsgcWSConnection);
    procedure WSServerDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSServerError(Connection: TsgcWSConnection; const Error: string);
    procedure WSServerMessage(Connection: TsgcWSConnection; const Text: string);
    procedure WSServerShutdown(Sender: TObject);
    procedure WSServerStartup(Sender: TObject);
  private
    procedure DoLog(const Text: string);
  private
    procedure DoSaveToken(const aAuth2: TsgcHTTPOAuth2Request);
    procedure DoLoadToken;
  public
    procedure DoStart;
    procedure DoStop;
  end;

var
  FRMOAuth2Server: TFRMOAuth2Server;

implementation

uses
  INIFiles,
  sgcHTTP_OAuth_Types;

{$R *.dfm}

procedure TFRMOAuth2Server.btnStartClick(Sender: TObject);
begin
  DoStart;
end;

procedure TFRMOAuth2Server.btnStopClick(Sender: TObject);
begin
  DoStop;
end;

procedure TFRMOAuth2Server.DoLoadToken;
var
  oINI: TINIFile;
  vAccessToken, vRefreshToken: string;
  vExpires: TDateTime;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    vAccessToken := oINI.ReadString(txtAppName.Text, 'Token', '');
    if vAccessToken <> '' then
    begin
      vRefreshToken := oINI.ReadString(txtAppName.Text, 'RefreshToken', '');
      vExpires := oINI.ReadDateTime(txtAppName.Text, 'Expires', 0);

      OAuth2.AddToken(txtAppName.Text, vAccessToken, vExpires, vRefreshToken);
    end;
  Finally
    oINI.Free;
  End;
end;

procedure TFRMOAuth2Server.DoLog(const Text: string);
begin
  TThread.Queue(nil, procedure
    begin
      if Assigned(memoLog) then
        memoLog.Lines.Add(Text);
    end);
end;

procedure TFRMOAuth2Server.DoSaveToken(const aAuth2: TsgcHTTPOAuth2Request);
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    oINI.WriteString(aAuth2.App.AppName, 'Token', aAuth2.Token.AccessToken);
    oINI.WriteString(aAuth2.App.AppName, 'RefreshToken',
      aAuth2.Token.RefreshToken);
    oINI.WriteDateTime(aAuth2.App.AppName, 'Expires', aAuth2.Token.Expires);
  Finally
    oINI.Free;
  End;
end;

procedure TFRMOAuth2Server.DoStart;
begin
  // ... OAuth2
  WSServer.Authentication.OAuth.OAuth2 := nil;
  WSServer.Authentication.Enabled := chkOAuth2.Checked;
  if chkOAuth2.Checked then
  begin
    OAuth2.Apps.Clear;
    OAuth2.Apps.AddApp(txtAppName.Text, txtRedirectURI.Text, txtClientId.Text,
      txtClientSecret.Text);
    WSServer.Authentication.Enabled := True;
    WSServer.Authentication.OAuth.OAuth2 := OAuth2;
    // ... load token from INIFile to recover the token if server has been restarted
    DoLoadToken;
  end;

  // ... start server
  WSServer.Port := StrToInt(txtDefaultPort.Text);
  WSServer.SSLOptions.Port := StrToInt(txtDefaultPort.Text);
  WSServer.SSLOptions.CertFile := 'sgc.pem';
  WSServer.SSLOptions.KeyFile := 'sgc.pem';
  WSServer.SSLOptions.RootCertFile := 'sgc.pem';
  WSServer.SSL := True;
  WSServer.Active := True;
end;

procedure TFRMOAuth2Server.DoStop;
begin
  WSServer.Active := False;
end;

procedure TFRMOAuth2Server.OAuth2OAuth2AfterAccessToken(Sender: TObject;
Connection: TsgcWSConnection; OAuth2: TsgcHTTPOAuth2Request; aResponse: string);
begin
  DoLog('Access Token Issued');

  // ... save token in INIFile to recover the token if server is restarted
  DoSaveToken(OAuth2);
end;

procedure TFRMOAuth2Server.OAuth2OAuth2AfterValidateAccessToken(Sender: TObject;
Connection: TsgcWSConnection; OAuth2: TsgcHTTPOAuth2Request;
var IsValid: Boolean);
begin
  if IsValid then
    DoLog('Token Valid: ' + Connection.Guid)
  else
    DoLog('Token Invalid: ' + Connection.Guid);
end;

procedure TFRMOAuth2Server.OAuth2OAuth2Authentication
  (Connection: TsgcWSConnection; OAuth2: TsgcHTTPOAuth2Request;
aUser, aPassword: string; var Authenticated: Boolean);
begin
  if (aUser = 'user') and (aPassword = 'secret') then
  begin
    Authenticated := True;
    DoLog('#authentication OK');
  end
  else
    DoLog('#authentication ERROR');
end;

procedure TFRMOAuth2Server.WSServerCommandGet(AContext: TIdContext;
ARequestInfo: TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
begin
  if ARequestInfo.Document = '/' then
  begin
    AResponseInfo.ContentText :=
      '<HTML><HEADER><TITLE>sgcWebSockets Test Page</TITLE></HEADER><BODY>Test Page</BODY></HTML>';
    AResponseInfo.ContentType := 'text/html';
    AResponseInfo.ResponseNo := 200;
  end
  else
    AResponseInfo.ResponseNo := 404;
end;

procedure TFRMOAuth2Server.WSServerConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;

procedure TFRMOAuth2Server.WSServerDisconnect(Connection: TsgcWSConnection;
Code: Integer);
begin
  DoLog('#disconnected');
end;

procedure TFRMOAuth2Server.WSServerError(Connection: TsgcWSConnection;
const Error: string);
begin
  DoLog('#error: ' + Error);
end;

procedure TFRMOAuth2Server.WSServerMessage(Connection: TsgcWSConnection;
const Text: string);
begin
  DoLog(Text);
end;

procedure TFRMOAuth2Server.WSServerShutdown(Sender: TObject);
begin
  DoLog('#server shutdown');
end;

procedure TFRMOAuth2Server.WSServerStartup(Sender: TObject);
begin
  DoLog('#server started');
end;

end.
```

