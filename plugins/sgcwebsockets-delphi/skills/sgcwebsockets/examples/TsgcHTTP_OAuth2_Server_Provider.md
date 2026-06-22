# TsgcHTTP_OAuth2_Server_Provider - Example

Full source of `FOAuth2_Server.pas` from the **20.HTTP_Protocol/08.OAuth2_ServerProvider** demo, which uses `TsgcHTTP_OAuth2_Server_Provider`.

API reference: [TsgcHTTP_OAuth2_Server_Provider](../reference/api/TsgcHTTP_OAuth2_Server_Provider.md)
Source demo: `20.HTTP_Protocol/08.OAuth2_ServerProvider` (file `FOAuth2_Server.pas`)

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
  sgcIdContext, sgcIdCustomHTTPServer, sgcSocket_Classes;

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
    Label6: TLabel;
    Label7: TLabel;
    txtClientId: TEdit;
    txtClientSecret: TEdit;
    txtTenant: TEdit;
    chkOAuth2: TCheckBox;
    WSServer: TsgcWebSocketHTTPServer;
    OAuth2Provider: TsgcHTTP_OAuth2_Server_Provider;
    Label5: TLabel;
    txtScope: TEdit;
    Label8: TLabel;
    Label9: TLabel;
    txtURL: TEdit;
    txtCallbackURL: TEdit;
    pnlBrowsers: TPanel;
    btnPublicPage: TButton;
    btnPrivatePage: TButton;
    procedure btnPrivatePageClick(Sender: TObject);
    procedure btnPublicPageClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure OAuth2ProviderOAuth2IsPrivateEndpoint(Sender: TObject; const
        aEndpoint: string; var IsPrivate: Boolean);
    procedure OAuth2ProviderOAuth2ProviderTokenUnknown(Sender: TObject; Connection:
        TsgcWSConnection; Endpoint: string; Response:
        TsgcHTTPOAuth2ProviderResponse);
    procedure OAuth2ProviderOAuth2ProviderTokenValid(Sender: TObject; Connection:
        TsgcWSConnection; Token: TsgcHTTPOAuth2ProviderToken; Response:
        TsgcHTTPOAuth2ProviderResponse);
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
    procedure DoOpenBrowser(const aEndpoint: string);
  public
    procedure DoStart;
    procedure DoStop;
  end;

var
  FRMOAuth2Server: TFRMOAuth2Server;

implementation

uses
  ShellAPI;

type
  TsgcWSConnectionOAuth2 = class(TsgcWSConnection_Base_Indy);

{$R *.dfm}

procedure TFRMOAuth2Server.btnPrivatePageClick(Sender: TObject);
begin
  DoOpenBrowser('/private');
end;

procedure TFRMOAuth2Server.btnPublicPageClick(Sender: TObject);
begin
  DoOpenBrowser('/public');
end;

procedure TFRMOAuth2Server.btnStartClick(Sender: TObject);
begin
  DoStart;
end;

procedure TFRMOAuth2Server.btnStopClick(Sender: TObject);
begin
  DoStop;
end;

procedure TFRMOAuth2Server.DoLog(const Text: string);
begin
  TThread.Queue(nil,
    procedure
    begin
      if Assigned(memoLog) then
        memoLog.Lines.Add(Text);
    end);
end;

procedure TFRMOAuth2Server.DoOpenBrowser(const aEndpoint: string);
begin
  {$IFDEF UNICODE}
    ShellExecute(Application.Handle, 'open', PWideChar('chrome'),
      PWideChar('https://' + txtHost.Text + ':' + txtDefaultPort.Text + aEndpoint), '', 0);
  {$ELSE}
    ShellExecute(Application.Handle, 'open', PAnsiChar('chrome'),
      PAnsiChar('https://' + txtHost.Text + ':' + txtDefaultPort.Text + aEndpoint), '', 0);
  {$ENDIF}
end;

procedure TFRMOAuth2Server.DoStart;
begin
  if txtTenant.Text = '' then
    raise Exception.Create('Set the Tenant First!!!');
  if txtClientId.Text = '' then
    raise Exception.Create('Set the Client ID First!!!');
  if txtClientSecret.Text = '' then
    raise Exception.Create('Set the Client Secret First!!!');

  // ... oauth2 Azure AD
  WSServer.Authentication.Enabled := True;
  OAuth2Provider.ClearProviders;
  OAuth2Provider.RegisterProvider(
    'azure',
    txtClientId.Text,
    txtClientSecret.Text,
    Format('https://login.microsoftonline.com/%s/oauth2/v2.0/authorize', [txtTenant.Text]),
    Format('https://login.microsoftonline.com/%s/oauth2/v2.0/token', [txtTenant.Text]),
    txtScope.Text,
    txtURL.Text,
    txtCallbackURL.Text
    );

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

procedure TFRMOAuth2Server.OAuth2ProviderOAuth2IsPrivateEndpoint(Sender:
    TObject; const aEndpoint: string; var IsPrivate: Boolean);
begin
  // ... configure here which endpoints are private
  if aEndpoint = '/private' then
    IsPrivate := True;
end;

procedure TFRMOAuth2Server.OAuth2ProviderOAuth2ProviderTokenUnknown(Sender:
    TObject; Connection: TsgcWSConnection; Endpoint: string; Response:
    TsgcHTTPOAuth2ProviderResponse);
begin
  // ... if token is unknown, redirect to login
  if EndPoint = '/private' then
    Response.RedirectURL := 'https://' + txtHost.Text + ':' + txtDefaultPort.Text + txtURL.Text;
end;

procedure TFRMOAuth2Server.OAuth2ProviderOAuth2ProviderTokenValid(Sender:
    TObject; Connection: TsgcWSConnection; Token: TsgcHTTPOAuth2ProviderToken;
    Response: TsgcHTTPOAuth2ProviderResponse);
begin
  DoLog('#Public Token: ' + Token.ID);
  DoLog('#Private Azure OAuth2 Token: ' + Token.AccessToken);

  Response.RedirectURL := 'https://localhost/private';
end;

procedure TFRMOAuth2Server.WSServerCommandGet(AContext: TIdContext;
ARequestInfo: TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
begin
  if ARequestInfo.Document = '/public' then
  begin
    AResponseInfo.ContentText :=
      '<HTML><HEADER><TITLE>Public Test Page</TITLE></HEADER><BODY>Public Test Page</BODY></HTML>';
    AResponseInfo.ContentType := 'text/html';
    AResponseInfo.ResponseNo := 200;
  end
  else if ARequestInfo.Document = '/private' then
  begin
    // return OAuth2 profile data
    AResponseInfo.ContentText := OAuth2Provider.Get(ARequestInfo, 'https://graph.microsoft.com/v1.0/me');
    AResponseInfo.ContentType := 'application/json';
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

