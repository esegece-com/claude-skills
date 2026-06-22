# TsgcWebSocketHTTPServer - Example

Full source of `uServerChat.pas` from the **01.WebSocket_Quick_Start/01.Server_and_Client_Chat** demo, which uses `TsgcWebSocketHTTPServer`.

API reference: [TsgcWebSocketHTTPServer](../reference/api/TsgcWebSocketHTTPServer.md)
Source demo: `01.WebSocket_Quick_Start/01.Server_and_Client_Chat` (file `uServerChat.pas`)

```pascal
unit uServerChat;
{$I ..\..\..\Source\sgcVer.inc}

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, HTTPApp, HTTPProd,
{$IFDEF SGC_INDY}sgcIdContext{$ELSE}IdContext{$ENDIF},
{$IFDEF SGC_INDY}sgcIdCustomHTTPServer{$ELSE}IdCustomHTTPServer{$ENDIF},
{$IFDEF SGC_INDY}sgcIdSSLOpenSSL{$ELSE}IdSSLOpenSSL{$ENDIF},
  sgcWebSocket_Classes, sgcWebSocket_Server, sgcWebSocket, sgcWebSocket_Const,
  sgcWebSocket_Classes_Indy, sgcBase_Classes, sgcTCP_Classes,
  sgcWebSocket_Types,
  sgcSocket_Classes;

type
  TfrmServerChat = class(TForm)
    pnlServer: TPanel;
    btnStop: TButton;
    btnStart: TButton;
    memoLog: TMemo;
    btnChrome: TButton;
    btnFirefox: TButton;
    btnSafari: TButton;
    btnEdge: TButton;
    chkCompressed: TCheckBox;
    pnlServerActive: TPanel;
    pnlServerOptions: TPanel;
    chkSSL: TCheckBox;
    Label1: TLabel;
    pnlBrowsers: TPanel;
    pageChat: TPageProducer;
    WSServer: TsgcWebSocketHTTPServer;
    txtHost: TEdit;
    Label2: TLabel;
    pageJQueryMobileCSS: TPageProducer;
    pageJQuery: TPageProducer;
    pageJQueryMobile: TPageProducer;
    txtDefaultPort: TEdit;
    Label3: TLabel;
    Default: TLabel;
    txtSSLPort: TEdit;
    Label4: TLabel;
    chkAuthentication: TCheckBox;
    txtAuthUser: TEdit;
    txtAuthPassword: TEdit;
    chkFlash: TCheckBox;
    chkSSE: TCheckBox;
    Label5: TLabel;
    Label6: TLabel;
    cboOpenSSLAPI: TComboBox;
    Label7: TLabel;
    cboTLSVersion: TComboBox;
    Label8: TLabel;
    chkECDHE: TCheckBox;
    chkHTTP2: TCheckBox;
    procedure FormCreate(Sender: TObject);
    procedure btnChromeClick(Sender: TObject);
    procedure btnEdgeClick(Sender: TObject);
    procedure btnFirefoxClick(Sender: TObject);
    procedure btnSafariClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure chkAuthenticationClick(Sender: TObject);
    procedure chkCompressedClick(Sender: TObject);
    procedure chkFlashClick(Sender: TObject);
    procedure chkSSEClick(Sender: TObject);
    procedure pageChatHTMLTag(Sender: TObject; Tag: TTag;
      const TagString: string; TagParams: TStrings; var ReplaceText: string);
    procedure WSServerAuthentication(Connection: TsgcWSConnection;
      aUser, aPassword: string; var Authenticated: Boolean);
    procedure WSServerCommandGet(AContext: TIdContext;
      ARequestInfo: TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
    procedure WSServerConnect(Connection: TsgcWSConnection);
    procedure WSServerError(Connection: TsgcWSConnection; const Error: string);
    procedure WSServerMessage(Connection: TsgcWSConnection; const Text: string);
    procedure WSServerDisconnect(Connection: TsgcWSConnection; Code: Integer);
  private
    FRequestSSL: Boolean;
    procedure DoOpenBrowser(const aBrowserName: string);
    { Private declarations }
  public
    { Public declarations }
  end;

var
  frmServerChat: TfrmServerChat;

implementation

uses
  ShellAPI;

{$R *.dfm}

procedure TfrmServerChat.FormCreate(Sender: TObject);
begin
  btnStart.Click;
  WSServer.DocumentRoot := ExtractFilePath(Application.ExeName);
end;

procedure TfrmServerChat.btnChromeClick(Sender: TObject);
begin
  DoOpenBrowser('chrome');
end;

procedure TfrmServerChat.btnEdgeClick(Sender: TObject);
begin
  DoOpenBrowser('msedge');
end;

procedure TfrmServerChat.btnFirefoxClick(Sender: TObject);
begin
  DoOpenBrowser('firefox');
end;

procedure TfrmServerChat.btnSafariClick(Sender: TObject);
begin
  DoOpenBrowser('safari');
end;

procedure TfrmServerChat.btnStartClick(Sender: TObject);
begin
  if chkSSL.Checked then
    WSServer.Port := StrToInt(txtSSLPort.Text)
  else
    WSServer.Port := StrToInt(txtDefaultPort.Text);

  // ... bindings
  With WSServer.Bindings.Add do
  begin
    Port := StrToInt(txtDefaultPort.Text);
    IP := txtHost.Text;
  end;

  WSServer.HTTP2Options.Enabled := chkHTTP2.Checked;
  if WSServer.HTTP2Options.Enabled then
  begin
    WSServer.SSLOptions.IOHandler := iohOpenSSL;
    WSServer.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_1_1;
    WSServer.SSLOptions.Version := tls1_3;
  end
  else
  begin
    case cboOpenSSLAPI.ItemIndex of
      0:
        begin
          WSServer.SSLOptions.IOHandler := iohOpenSSL;
          WSServer.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_1_0;
        end;
      1:
        begin
          WSServer.SSLOptions.IOHandler := iohOpenSSL;
          WSServer.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_1_1;
        end;
      2:
        begin
          WSServer.SSLOptions.IOHandler := iohOpenSSL;
          WSServer.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_3_0;
        end;
      3:
        WSServer.SSLOptions.IOHandler := iohSChannel;
    end;
    if cboOpenSSLAPI.ItemIndex = 3 then
    begin
      WSServer.SSLOptions.CertFile := 'sgc_schannel.pfx';
      WSServer.SSLOptions.KeyFile := '';
      WSServer.SSLOptions.RootCertFile := '';
      WSServer.SSLOptions.Password := '1234';
    end
    else
    begin
      WSServer.SSLOptions.CertFile := 'sgc.pem';
      WSServer.SSLOptions.KeyFile := 'sgc.pem';
      WSServer.SSLOptions.RootCertFile := 'sgc.pem';
      WSServer.SSLOptions.Password := '';
    end;
    case cboTLSVersion.ItemIndex of
      0:
        WSServer.SSLOptions.Version := tlsUndefined;
      1:
        WSServer.SSLOptions.Version := tls1_0;
      2:
        WSServer.SSLOptions.Version := tls1_1;
      3:
        WSServer.SSLOptions.Version := tls1_2;
      4:
        WSServer.SSLOptions.Version := tls1_3;
    end;
  end;

  WSServer.SSLOptions.OpenSSL_Options.ECDHE := chkECDHE.Checked;
  WSServer.SSL := chkSSL.Checked;

  if chkSSL.Checked then
  begin
    With WSServer.Bindings.Add do
    begin
      Port := StrToInt(txtSSLPort.Text);
      IP := txtHost.Text;
    end;
    WSServer.SSLOptions.Port := StrToInt(txtSSLPort.Text);
  end;
  if chkFlash.Checked then
  begin
    With WSServer.Bindings.Add do
    begin
      Port := 843;
      IP := txtHost.Text;
    end;
  end;

  // ... active
  WSServer.Active := True;
  if WSServer.Active then
  begin
    memoLog.Lines.Add('#Server Started: ' + txtHost.Text + ':' +
      IntToStr(WSServer.Port));
    if chkFlash.Checked then
      memoLog.Lines.Add('#Flash FallBack Enabled');
    if chkSSE.Checked then
      memoLog.Lines.Add('#SSE FallBack Enabled');
    if chkSSL.Checked then
    begin
      if cboOpenSSLAPI.ItemIndex = 3 then
        memoLog.Lines.Add('#SSL Enabled (SChannel)')
      else
        memoLog.Lines.Add('#SSL Enabled (OpenSSL)');
    end;
    if chkHTTP2.Checked then
      memoLog.Lines.Add('#HTTP/2 Enabled');
    if chkCompressed.Checked then
      memoLog.Lines.Add('#Compression Enabled');
    if chkAuthentication.Checked then
      memoLog.Lines.Add('#Authentication Enabled');
    pnlServerOptions.Enabled := False;
    pnlBrowsers.Enabled := True;
  end;
end;

procedure TfrmServerChat.btnStopClick(Sender: TObject);
begin
  WSServer.Active := False;
  WSServer.Bindings.Clear;

  if not WSServer.Active then
  begin
    memoLog.Lines.Add('#Server Stopped');
    pnlServerOptions.Enabled := True;
    pnlBrowsers.Enabled := False;
  end;

  if WSServer.SSLOptions.IOHandler <> iohSChannel then
    UnLoadOpenSSLLibrary;
end;

procedure TfrmServerChat.chkAuthenticationClick(Sender: TObject);
begin
  WSServer.Authentication.Enabled := chkAuthentication.Checked;
end;

procedure TfrmServerChat.chkCompressedClick(Sender: TObject);
begin
  WSServer.Extensions.PerMessage_Deflate.Enabled := chkCompressed.Checked;
end;

procedure TfrmServerChat.chkFlashClick(Sender: TObject);
begin
  WSServer.FallBack.Flash.Enabled := chkFlash.Checked;
end;

procedure TfrmServerChat.chkSSEClick(Sender: TObject);
begin
  WSServer.FallBack.ServerSentEvents.Enabled := chkSSE.Checked;
end;

procedure TfrmServerChat.DoOpenBrowser(const aBrowserName: string);
var
  vHTTP, vPort: string;
begin
  vHTTP := 'http';
  vPort := txtDefaultPort.Text;
  if chkSSL.Checked then
  begin
    vHTTP := 'https';
    vPort := txtSSLPort.Text;
  end;

{$IFDEF UNICODE}
  ShellExecute(Application.Handle, 'open', PWideChar(aBrowserName),
    PWideChar(vHTTP + '://' + txtHost.Text + ':' + vPort), '', 0);
{$ELSE}
  ShellExecute(Application.Handle, 'open', PAnsiChar(aBrowserName),
    PAnsiChar(vHTTP + '://' + txtHost.Text + ':' + vPort), '', 0);
{$ENDIF}
end;

procedure TfrmServerChat.pageChatHTMLTag(Sender: TObject; Tag: TTag;
  const TagString: string; TagParams: TStrings; var ReplaceText: string);
begin
  if TagString = 'port' then
  begin
    if FRequestSSL then
      ReplaceText := txtSSLPort.Text
    else
      ReplaceText := txtDefaultPort.Text;
  end
  else if TagString = 'host' then
    ReplaceText := txtHost.Text
  else if TagString = 'ssl' then
  begin
    if FRequestSSL then
      ReplaceText := 's'
    else
      ReplaceText := '';
  end
  else if TagString = 'authentication' then
    ReplaceText := CS_AUTH_URL + txtAuthUser.Text + '/' + txtAuthPassword.Text;
end;

procedure TfrmServerChat.WSServerAuthentication(Connection: TsgcWSConnection;
  aUser, aPassword: string; var Authenticated: Boolean);
begin
  memoLog.Lines.Add('#Authentication: ' + aUser + ':' + aPassword);
end;

procedure TfrmServerChat.WSServerCommandGet(AContext: TIdContext;
  ARequestInfo: TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo);
begin
  if ARequestInfo.Document = '/jquery.mobile.css' then
  begin
    AResponseInfo.ContentText := pageJQueryMobileCSS.Content;
    AResponseInfo.ContentType := 'text/css';
    AResponseInfo.ResponseNo := 200;
  end
  else if ARequestInfo.Document = '/jquery.js' then
  begin
    AResponseInfo.ContentText := pageJQuery.Content;
    AResponseInfo.ContentType := 'text/javascript';
    AResponseInfo.ResponseNo := 200;
  end
  else if ARequestInfo.Document = '/jquery.mobile.js' then
  begin
    AResponseInfo.ContentText := pageJQueryMobile.Content;
    AResponseInfo.ContentType := 'text/javascript';
    AResponseInfo.ResponseNo := 200;
  end
  else
  begin
    FRequestSSL := chkSSL.Checked;
    AResponseInfo.ContentText := pageChat.Content;
    AResponseInfo.ContentType := 'text/html';
    AResponseInfo.ResponseNo := 200;
  end;
end;

procedure TfrmServerChat.WSServerConnect(Connection: TsgcWSConnection);
begin
  memoLog.Lines.Add('Connected: ' + Connection.IP);
end;

procedure TfrmServerChat.WSServerDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  memoLog.Lines.Add('Disconnected (' + IntToStr(Code) + '): ' + Connection.IP);
end;

procedure TfrmServerChat.WSServerError(Connection: TsgcWSConnection;
  const Error: string);
begin
  memoLog.Lines.Add('Error: ' + Connection.IP + ' - ' + Error);
end;

procedure TfrmServerChat.WSServerMessage(Connection: TsgcWSConnection;
  const Text: string);
begin
  memoLog.Lines.Add(Connection.IP + ':' + Text);
  WSServer.Broadcast(Text);
end;

end.
```

