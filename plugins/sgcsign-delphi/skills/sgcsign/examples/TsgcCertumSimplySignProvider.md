# TsgcCertumSimplySignProvider - Example

Full source of `frmMain.pas` from the **KeyProvider_Certum** demo, which uses `TsgcCertumSimplySignProvider`.

API reference: [TsgcCertumSimplySignProvider](../reference/api/TsgcCertumSimplySignProvider.md)
Source demo: `KeyProvider_Certum` (file `frmMain.pas`)

```pascal
{ ***************************************************************************
  sgcSign component

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit frmMain;

interface

uses
  Windows, Messages, SysUtils, Classes,
  Graphics, Controls, Forms, Dialogs,
  StdCtrls, ExtCtrls,
  // sgcSign
  sgcSign_Types, sgcSign_Interfaces, sgcSign_Classes,
  sgcSign_CAdES, sgcSign_KeyProvider_Certum;

type
  TFormMain = class(TForm)
    pnlTop: TPanel;
    lblClientId: TLabel;
    edClientId: TEdit;
    lblClientSecret: TLabel;
    edClientSecret: TEdit;
    lblUsername: TLabel;
    edUsername: TEdit;
    lblPassword: TLabel;
    edPassword: TEdit;
    lblPIN: TLabel;
    edPIN: TEdit;
    lblBaseURL: TLabel;
    edBaseURL: TEdit;
    btnConnect: TButton;
    btnListCerts: TButton;
    pnlClient: TPanel;
    lblData: TLabel;
    memoData: TMemo;
    lblSignature: TLabel;
    memoSignature: TMemo;
    btnSign: TButton;
    lblLog: TLabel;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure btnConnectClick(Sender: TObject);
    procedure btnListCertsClick(Sender: TObject);
    procedure btnSignClick(Sender: TObject);
  private
    FProvider: TsgcCertumSimplySignProvider;
    procedure Log(const aMsg: string);
  end;

var
  FormMain: TFormMain;

implementation

{$R *.dfm}

procedure TFormMain.FormCreate(Sender: TObject);
begin
  FProvider := nil;
  edBaseURL.Text := 'https://cloudsign.certum.eu';
  Log('Certum SimplySign demo ready. Enter credentials and connect.');
end;

procedure TFormMain.btnConnectClick(Sender: TObject);
begin
  if Trim(edClientId.Text) = '' then
  begin
    Log('ERROR: Please enter Client ID');
    Exit;
  end;

  if Trim(edUsername.Text) = '' then
  begin
    Log('ERROR: Please enter Username');
    Exit;
  end;

  if Trim(edPassword.Text) = '' then
  begin
    Log('ERROR: Please enter Password');
    Exit;
  end;

  Log('Connecting to Certum SimplySign...');

  if FProvider <> nil then
    FreeAndNil(FProvider);

  FProvider := TsgcCertumSimplySignProvider.Create(nil);
  try
    FProvider.ClientId := edClientId.Text;
    FProvider.ClientSecret := edClientSecret.Text;
    FProvider.Username := edUsername.Text;
    FProvider.Password := edPassword.Text;
    FProvider.PIN := edPIN.Text;
    FProvider.BaseURL := edBaseURL.Text;
    FProvider.Connect;
    Log('SUCCESS: Connected to Certum SimplySign');
    Log('Certificate: ' + FProvider.Certificate.Subject);
  except
    on E: Exception do
    begin
      Log('ERROR: ' + E.Message);
      FreeAndNil(FProvider);
    end;
  end;
end;

procedure TFormMain.btnListCertsClick(Sender: TObject);
var
  vJSON: string;
begin
  if FProvider = nil then
  begin
    Log('ERROR: Please connect first');
    Exit;
  end;

  Log('Listing certificates...');
  try
    vJSON := FProvider.ListCertificates;
    Log('Certificates: ' + vJSON);
  except
    on E: Exception do
      Log('ERROR: ' + E.Message);
  end;
end;

procedure TFormMain.btnSignClick(Sender: TObject);
var
  vSigner: TsgcCAdESSigner;
  vData: TBytes;
  vBase64: string;
begin
  if FProvider = nil then
  begin
    Log('ERROR: Please connect to Certum first');
    Exit;
  end;

  if Trim(memoData.Lines.Text) = '' then
  begin
    Log('ERROR: Please enter data to sign');
    Exit;
  end;

  Log('Signing with Certum SimplySign...');

  vSigner := TsgcCAdESSigner.Create(nil);
  try
    try
      vSigner.KeyProvider := FProvider as IsgcKeyProvider;
      vSigner.Level := clBES;
      vSigner.Detached := True;

      vData := TEncoding.UTF8.GetBytes(memoData.Lines.Text);
      vBase64 := vSigner.SignDataBase64(vData);
      memoSignature.Lines.Text := vBase64;

      Log('SUCCESS: Data signed with CAdES-BES using Certum');
    except
      on E: Exception do
        Log('ERROR: ' + E.Message);
    end;
  finally
    vSigner.Free;
  end;
end;

procedure TFormMain.Log(const aMsg: string);
begin
  memoLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) + ' ' + aMsg);
end;

end.
```

