# TIdSASLXOAuth2 - Example

Full source of `fSmtpClient.pas` from the **SmtpClient** demo, which uses `TIdSASLXOAuth2`.

API reference: [TIdSASLXOAuth2](../reference/api/TIdSASLXOAuth2.md)
Source demo: `SmtpClient` (file `fSmtpClient.pas`)

```pascal
unit fsmtpClient;

interface

{.$DEFINE SGC_WEBSOCKETS}

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls, IdIOHandlerSocket,
  IdIOHandlerStack, IdSSLOpenSSL, IdSMTP, IdMessage, IdIOHandler,
  IdExplicitTLSClientServerBase, Web.HTTPApp, Web.HTTPProd, IdMessageBuilder,
  IdComponent, IdTCPConnection, IdTCPClient, IdMessageClient, IdSMTPBase,
  IdBaseComponent, IdSSL, IdSSLOpenSSLHeaders, ExtCtrls, ComCtrls,
  IdSASL, IdSASLXOAUTH2
  {$IFDEF SGC_WEBSOCKETS}
  ,sgcBase_Classes, sgcHTTP_Classes, sgcHTTP_OAuth_Client,
  sgcHTTP_OAuth2_Client, sgcHTTP, sgcHTTP_OAuth_Types
  {$ENDIF};

type
  TfrmsmtpClient = class(TForm)
    openssl: TIdSSLIOHandlerSocketOpenSSL;
    btnSendEmail: TButton;
    txtHost: TEdit;
    lblHost: TLabel;
    lblPort: TLabel;
    txtPort: TEdit;
    memoLog: TMemo;
    cboOpenSSLAPI: TComboBox;
    cboTLSVersion: TComboBox;
    lblSSL: TLabel;
    smtp: TIdSMTP;
    Label1: TLabel;
    txtUsername: TEdit;
    Label2: TLabel;
    txtPassword: TEdit;
    txtEmailTo: TEdit;
    Label3: TLabel;
    PageControl1: TPageControl;
    tabUserPassword: TTabSheet;
    Panel1: TPanel;
    Panel2: TPanel;
    tabXOAUTH2: TTabSheet;
    xoauth2: TIdSASLXOAUTH2;
    memoXOAuth2Token: TMemo;
    Label4: TLabel;
    txtXOAuth2User: TEdit;
    Label5: TLabel;
    Label6: TLabel;
    txtOAuth2ClientId: TEdit;
    Label7: TLabel;
    txtOAuth2ClientSecret: TEdit;
    procedure FormCreate(Sender: TObject);
    procedure btnSendEmailClick(Sender: TObject);
    procedure opensslStatus(ASender: TObject; const AStatus:
        TIdStatus; const AStatusText: string);
    procedure opensslStatusInfo(const AMsg: string);
    procedure IdSSLIOHandlerSocketOpenSSL1StatusInfoEx(ASender: TObject; const
        AsslSocket: PSSL; const AWhere, Aret: Integer; const AType, AMsg: string);
    procedure xoauth2Authenticate(Sender: TObject; var Username, Token: string);
  {$IFDEF SGC_WEBSOCKETS}
  private
    FOAuth2: TsgcHTTP_OAuth2_Client;
    function GetOAuth2: TsgcHTTP_OAuth2_Client;
    procedure OnAfterAccessTokenEvent(Sender: TObject; const Access_Token,
        Token_Type, Expires_In, Refresh_Token, Scope, RawParams: String; var
        Handled: Boolean);
    procedure DoGetOAuth2Token;
  protected
    property OAuth2: TsgcHTTP_OAuth2_Client read GetOAuth2 write FOAuth2;
  {$ENDIF}

  private
    procedure DoSendEmail(const aTo, aSubject, aMessage: string);
  public
    procedure DoLog(const aText: string);
  end;

var
  frmsmtpClient: TfrmsmtpClient;

implementation

{$R *.dfm}

procedure TfrmsmtpClient.FormCreate(Sender: TObject);
begin
  {$IFDEF SGC_WEBSOCKETS}
  txtOAuth2ClientId.Enabled := True;
  txtOAuth2ClientSecret.Enabled := True;
  {$ELSE}
  txtOAuth2ClientId.Enabled := False;
  txtOAuth2ClientSecret.Enabled := False;
  {$ENDIF}
end;

procedure TfrmsmtpClient.btnSendEmailClick(Sender: TObject);
begin
  if txtEmailTo.Text = '' then
    raise Exception.Create('Mail To is required!!!');

  smtp.Host := txtHost.Text;
  smtp.Port := StrToInt(txtPort.Text);
  smtp.Username := txtUsername.Text;
  smtp.Password := txtPassword.Text;
  smtp.IOHandler := openssl;
  smtp.UseTLS := utUseExplicitTLS;

  openssl.SSLOptions.Mode := sslmUnassigned;
  openssl.SSLOptions.VerifyMode := [];
  openssl.SSLOptions.VerifyDepth := 0;

  case cboOpenSSLAPI.ItemIndex of
    0: openssl.SSLOptions.APIVersion := sslvAPI_1_0;
    1: openssl.SSLOptions.APIVersion := sslvAPI_1_1;
    2: openssl.SSLOptions.APIVersion := sslvAPI_3_0;
  end;

  case cboTLSVersion.ItemIndex of
    0,1: openssl.SSLOptions.Method := sslvTLSv1;
    2: openssl.SSLOptions.Method := sslvTLSv1_1;
    3: openssl.SSLOptions.Method := sslvTLSv1_2;
    4: openssl.SSLOptions.Method := sslvTLSv1_3;
  end;

  case PageControl1.ActivePageIndex of
    0:
      begin
        if txtUsername.Text = '' then
          raise Exception.Create('Username is required!!!');
        if txtPassword.Text = '' then
          raise Exception.Create('Password is required!!!');

        smtp.AuthType := satDefault;

        DoSendEmail(txtEmailTo.text, 'sgcIndy SMTP', 'Test Message');
      end;
    1:
      begin
        if txtXOAuth2User.Text = '' then
          raise Exception.Create('Username is required!!!');
        {$IFNDEF SGC_WEBSOCKETS}
        if memoXOAuth2Token.Text = '' then
          raise Exception.Create('Token is required!!!');
        {$ENDIF}

        smtp.AuthType := satSASL;
        smtp.SASLMechanisms.Clear;
        smtp.SASLMechanisms.Add.SASL := xoauth2;

        {$IFDEF SGC_WEBSOCKETS}
        DoGetOAuth2Token;
        {$ELSE}
        DoSendEmail(txtEmailTo.text, 'sgcIndy SMTP XOAuth2', 'Test Message');
        {$ENDIF}
      end;
  end;
end;


procedure TfrmsmtpClient.DoLog(const aText: string);
begin
  TThread.Queue(nil,
    procedure
    begin
	  if Assigned(memoLog) then
		  memoLog.Lines.Add(aText);
    end);
end;

procedure TfrmsmtpClient.opensslStatus(ASender: TObject; const
    AStatus: TIdStatus; const AStatusText: string);
begin
  DoLog(AStatusText);
end;

procedure TfrmsmtpClient.opensslStatusInfo(const AMsg: string);
begin
  DoLog(AMsg);
end;

procedure TfrmsmtpClient.IdSSLIOHandlerSocketOpenSSL1StatusInfoEx(ASender: TObject;
    const AsslSocket: PSSL; const AWhere, Aret: Integer; const AType, AMsg:
    string);
begin
  DoLog(AMsg);
end;

procedure TfrmsmtpClient.DoSendEmail(const aTo, aSubject, aMessage: string);
var
  oMessage: TIdMessage;
  oHTML: TIdMessageBuilderHtml;
begin
  oHTML := TIdMessageBuilderHtml.Create;
  Try
    oHTML.Html.Text := aMessage;

    oHTML.HtmlCharSet := 'utf-8';
    oMessage := oHTML.NewMessage(nil);

    oMessage.Recipients.Add;
    oMessage.Recipients[0].Address := aTo;
    oMessage.from.Address := txtUsername.Text;
    oMessage.Subject := aSubject;

    if not SMTP.connected then
      SMTP.Connect;
    SMTP.Send(oMessage);
    try
      SMTP.Disconnect(false);
    except
    end;
  Finally
    FreeAndNil(oHTML);
  End;
end;

{$IFDEF SGC_WEBSOCKETS}
procedure TfrmsmtpClient.DoGetOAuth2Token;
begin
  OAuth2.OAuth2Options.GrantType := auth2CodePKCE;
  OAuth2.LocalServerOptions.IP := '127.0.0.1';
  OAuth2.LocalServerOptions.Port := 0;

  OAuth2.AuthorizationServerOptions.AuthURL := 'https://accounts.google.com/o/oauth2/auth';
  OAuth2.AuthorizationServerOptions.TokenURL := 'https://accounts.google.com/o/oauth2/token';
  OAuth2.AuthorizationServerOptions.Scope.Text := 'https://mail.google.com/';

  OAuth2.OAuth2Options.ClientId := txtOAuth2ClientId.Text;
  OAuth2.OAuth2Options.ClientSecret := txtOAuth2ClientSecret.Text;

  OAuth2.Start;
end;


function TfrmsmtpClient.GetOAuth2: TsgcHTTP_OAuth2_Client;
begin
  if not Assigned(FOAuth2) then
  begin
    FOAuth2 := TsgcHTTP_OAuth2_Client.Create(self);
    FOAuth2.OnAfterAccessToken := OnAfterAccessTokenEvent;
  end;
  Result := FOAuth2;
end;

procedure TfrmsmtpClient.OnAfterAccessTokenEvent(Sender: TObject; const
    Access_Token, Token_Type, Expires_In, Refresh_Token, Scope, RawParams:
    String; var Handled: Boolean);
begin
  memoXOAuth2Token.Lines.Text := Access_Token;

  DoSendEmail(txtEmailTo.text, 'sgcIndy SMTP XOAuth2', 'Test Message');
end;
{$ENDIF}

procedure TfrmsmtpClient.xoauth2Authenticate(Sender: TObject; var Username,
    Token: string);
begin
  Username := txtXOAuth2User.Text;
  Token := memoXOAuth2Token.Lines.Text;
end;

end.
```

