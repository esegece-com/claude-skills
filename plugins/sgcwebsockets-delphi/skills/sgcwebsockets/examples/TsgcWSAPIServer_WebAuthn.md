# TsgcWSAPIServer_WebAuthn - Example

Full source of `FWebAuthn_Server.pas` from the **20.HTTP_Protocol/12.WebAuthn** demo, which uses `TsgcWSAPIServer_WebAuthn`.

API reference: [TsgcWSAPIServer_WebAuthn](../reference/api/TsgcWSAPIServer_WebAuthn.md)
Source demo: `20.HTTP_Protocol/12.WebAuthn` (file `FWebAuthn_Server.pas`)

```pascal
unit FWebAuthn_Server;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, StrUtils,
  // sgc
  sgcBase_Classes, sgcTCP_Classes, sgcWebSocket_Classes, sgcWebSocket_Types,
  sgcWebSocket_Classes_Indy, sgcWebSocket_Server, sgcWebSocket,
  sgcIdCustomHTTPServer, sgcSocket_Classes, sgcHTTP_Classes, sgcHTTP,
  sgcWebSocket_Server_API_WebAuthn, sgcWebSocket_Server_APIs,
  sgcWebAuthn_Classes, sgcWebAuthn_Types;

type
  TFRMWebAuthnServer = class(TForm)
    btnStart: TButton;
    btnStop: TButton;
    Label1: TLabel;
    Label2: TLabel;
    txtHost: TEdit;
    Label3: TLabel;
    Default: TLabel;
    txtDefaultPort: TEdit;
    pnlLeft: TPanel;
    pnlOptions: TPanel;
    memoLog: TMemo;
    Server: TsgcWebSocketHTTPServer;
    WebAuthnServer: TsgcWSAPIServer_WebAuthn;
    Label4: TLabel;
    pnlBrowsers: TPanel;
    btnChrome: TButton;
    btnEdge: TButton;
    btnFirefox: TButton;
    btnSafari: TButton;
    txtRelyingParty: TEdit;
    pnlTop: TPanel;
    procedure FormCreate(Sender: TObject);
    procedure btnChromeClick(Sender: TObject);
    procedure btnEdgeClick(Sender: TObject);
    procedure btnFirefoxClick(Sender: TObject);
    procedure btnSafariClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure serverShutdown(Sender: TObject);
    procedure serverStartup(Sender: TObject);
    procedure WebAuthnServerWebAuthnAuthenticationError(Sender: TObject; const
        aRequest: TsgcWebAuthn_AuthenticationVerify_Request; const aError: string);
    procedure WebAuthnServerWebAuthnAuthenticationOptionsRequest(Sender: TObject;
        const aRequest: TsgcWebAuthn_AuthenticationOptions_Request; var
        CredentialRecords: TsgcWebAuthn_CredentialRecords; var Accept: Boolean);
    procedure WebAuthnServerWebAuthnAuthenticationSuccessful(Sender: TObject; const
        aRequest: TsgcWebAuthn_AuthenticationVerify_Request; const aAuthentication:
        TsgcWebAuthn_Authentication; var Accept: Boolean);
    procedure WebAuthnServerWebAuthnException(Sender: TObject; E: Exception; var
        aResponseCode: Integer);
    procedure WebAuthnServerWebAuthnHTTPRequest(Sender: TObject; aMethod:
        TsgcWebAuthnHTTPRequestMethod; const aRequest: TsgcHTTPRequest; var Accept:
        Boolean);
    procedure WebAuthnServerWebAuthnHTTPResponse(Sender: TObject; aMethod:
        TsgcWebAuthnHTTPRequestMethod; const aRequest: TsgcHTTPRequest; const
        aResponse: TsgcHTTPResponse);
    procedure WebAuthnServerWebAuthnRegistrationError(Sender: TObject; const
        aRequest: TsgcWebAuthn_RegistrationVerify_Request; const aRegistration:
        TsgcWebAuthn_Registration; const aError: string);
    procedure WebAuthnServerWebAuthnRegistrationSuccessful(Sender: TObject; const
        aRegistration: TsgcWebAuthn_Registration; const aCredentialRecord:
        TsgcWebAuthn_CredentialRecord; var Accept: Boolean);
  private
    procedure DoLog(const aText: String);
    procedure DoOpenBrowser(const aBrowserName: string);
  public
    destructor Destroy; override;
  end;

var
  FRMWebAuthnServer: TFRMWebAuthnServer;

implementation

uses
  ShellAPI,
  sgcBase_Helpers;

{$R *.dfm}

procedure TFRMWebAuthnServer.FormCreate(Sender: TObject);
begin
  btnStart.Click;
end;

destructor TFRMWebAuthnServer.Destroy;
begin

  inherited;
end;

procedure TFRMWebAuthnServer.btnChromeClick(Sender: TObject);
begin
  DoOpenBrowser('chrome');
end;

procedure TFRMWebAuthnServer.btnEdgeClick(Sender: TObject);
begin
  DoOpenBrowser('msedge');
end;

procedure TFRMWebAuthnServer.btnFirefoxClick(Sender: TObject);
begin
  DoOpenBrowser('firefox');
end;

procedure TFRMWebAuthnServer.btnSafariClick(Sender: TObject);
begin
  DoOpenBrowser('safari');
end;

procedure TFRMWebAuthnServer.btnStartClick(Sender: TObject);
begin
  // ... enable for testing
  WebAuthnServer.EndpointsOptions.Test.Enabled := True;
  // ... WebAuthn options
  WebAuthnServer.WebAuthnOptions.RelyingParty := txtRelyingParty.text;
  // ... Fido Metadata Service
  WebAuthnServer.WebAuthnOptions.MDS.Enabled := True;
  WebAuthnServer.WebAuthnOptions.MDS.MDS_FileName := 'blob.jwt';
  WebAuthnServer.WebAuthnOptions.MDS.RootCert_FileName := 'root-r3.crt';
  WebAuthnServer.WebAuthnOptions.MDS.LeafCertificateCRL := True;

  // ... bindings
  Server.Port := StrToInt(txtDefaultPort.Text);
  Server.SSLOptions.Port := StrToInt(txtDefaultPort.Text);
  Server.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_3_0;
  Server.Bindings.Clear;
  With Server.Bindings.Add do
  begin
    Port := StrToInt(txtDefaultPort.Text);
    IP := txtHost.Text;
  end;
  Server.SSL := True;

  // ... active
  Server.Active := True;
end;

procedure TFRMWebAuthnServer.btnStopClick(Sender: TObject);
begin
  Server.Active := False;
end;

procedure TFRMWebAuthnServer.DoLog(const aText: String);
begin
  TThread.Queue(nil,
    procedure
    begin
      if Assigned(memoLog) then
        memoLog.Lines.Add(aText);
    end);
end;

procedure TFRMWebAuthnServer.DoOpenBrowser(const aBrowserName: string);
begin
{$IFDEF UNICODE}
  ShellExecute(Application.Handle, 'open', PWideChar(aBrowserName),
    PWideChar('https://' + txtRelyingParty.text + ':' + txtDefaultPort.Text +
    WebAuthnServer.EndpointsOptions.Test.Endpoint), '', 0);
{$ELSE}
  ShellExecute(Application.Handle, 'open', PAnsiChar(aBrowserName),
    PAnsiChar('https://' + txtRelyingParty.text + ':' + txtDefaultPort.Text +
    WebAuthnServer.EndpointsOptions.Test.Endpoint), '', 0);
{$ENDIF}
end;

procedure TFRMWebAuthnServer.serverShutdown(Sender: TObject);
begin
  DoLog('#Server Stopped: ' + txtHost.Text + ':' + txtDefaultPort.Text);
end;

procedure TFRMWebAuthnServer.serverStartup(Sender: TObject);
begin
  DoLog('#Server Started: ' + txtHost.Text + ':' + txtDefaultPort.Text);
end;

procedure TFRMWebAuthnServer.WebAuthnServerWebAuthnAuthenticationError(Sender:
    TObject; const aRequest: TsgcWebAuthn_AuthenticationVerify_Request; const
    aError: string);
begin
  DoLog('#webauthn_authentication_error: ' + aError);
end;

procedure
    TFRMWebAuthnServer.WebAuthnServerWebAuthnAuthenticationOptionsRequest(
    Sender: TObject; const aRequest:
    TsgcWebAuthn_AuthenticationOptions_Request; var CredentialRecords:
    TsgcWebAuthn_CredentialRecords; var Accept: Boolean);
var
  i: Integer;
  oList: TStringList;
  oCredentialRecord: TsgcWebAuthn_CredentialRecord;
begin
  if FileExists('credentials.txt') then
  begin
    oList := TStringList.Create;
    Try
      oList.LoadFromFile('credentials.txt');
      for i := 0 to oList.Count - 1 do
      begin
        if oList[i] <> '' then
        begin
          if aRequest.Username <> '' then
          begin
            oCredentialRecord := TsgcWebAuthn_CredentialRecord.Create;
            Try
              oCredentialRecord.ReadJSON(oList[i]);
              if oCredentialRecord.Username = aRequest.Username then
                CredentialRecords.AddCredentialRecordFromJSON(oList[i]);
            Finally
              oCredentialRecord.Free;
            End;
          end
          else
            CredentialRecords.AddCredentialRecordFromJSON(oList[i]);
        end;
      end;
    Finally
      oList.Free;
    End;
  end;
end;

procedure TFRMWebAuthnServer.WebAuthnServerWebAuthnAuthenticationSuccessful(
    Sender: TObject; const aRequest: TsgcWebAuthn_AuthenticationVerify_Request;
    const aAuthentication: TsgcWebAuthn_Authentication; var Accept: Boolean);
begin
  DoLog('#webauthn_authentication_successful');
end;

procedure TFRMWebAuthnServer.WebAuthnServerWebAuthnException(Sender: TObject;
    E: Exception; var aResponseCode: Integer);
begin
  DoLog('#exception: ' + E.Message);
end;

procedure TFRMWebAuthnServer.WebAuthnServerWebAuthnHTTPRequest(Sender: TObject;
    aMethod: TsgcWebAuthnHTTPRequestMethod; const aRequest: TsgcHTTPRequest;
    var Accept: Boolean);
begin
  Accept := True;
  DoLog('***RAW***' + #13#10 + aRequest.Content + #13#10);
end;

procedure TFRMWebAuthnServer.WebAuthnServerWebAuthnHTTPResponse(Sender:
    TObject; aMethod: TsgcWebAuthnHTTPRequestMethod; const aRequest:
    TsgcHTTPRequest; const aResponse: TsgcHTTPResponse);
begin
  DoLog('***REQUEST***' + #13#10 + aRequest.Content + #13#10 + '***RESPONSE***' + #13#10 + aResponse.Content);
end;

procedure TFRMWebAuthnServer.WebAuthnServerWebAuthnRegistrationError(Sender:
    TObject; const aRequest: TsgcWebAuthn_RegistrationVerify_Request; const
    aRegistration: TsgcWebAuthn_Registration; const aError: string);
begin
  DoLog('#webauthn_registration_error: ' + aError);
end;

procedure TFRMWebAuthnServer.WebAuthnServerWebAuthnRegistrationSuccessful(
    Sender: TObject; const aRegistration: TsgcWebAuthn_Registration; const
    aCredentialRecord: TsgcWebAuthn_CredentialRecord; var Accept: Boolean);
var
  oList: TStringList;
begin
  DoLog('#webauthn_registration_successful');

  oList := TStringList.Create;
  Try
    if FileExists('credentials.txt') then
      oList.LoadFromFile('credentials.txt');
    oList.Add(aCredentialRecord.AsJSON);
    oList.SaveToFile('credentials.txt');
  Finally
    oList.Free;
  End;
end;

end.
```

