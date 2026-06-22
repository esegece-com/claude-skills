# TsgcAzureTrustedSigningProvider - Example

Full source of `frmMain.pas` from the **KeyProvider_Azure** demo, which uses `TsgcAzureTrustedSigningProvider`.

API reference: [TsgcAzureTrustedSigningProvider](../reference/api/TsgcAzureTrustedSigningProvider.md)
Source demo: `KeyProvider_Azure` (file `frmMain.pas`)

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
  sgcSign_CAdES, sgcSign_KeyProvider_Azure;

type
  TFormMain = class(TForm)
    pnlTop: TPanel;
    lblTenantId: TLabel;
    edTenantId: TEdit;
    lblClientId: TLabel;
    edClientId: TEdit;
    lblClientSecret: TLabel;
    edClientSecret: TEdit;
    lblAccountName: TLabel;
    edAccountName: TEdit;
    lblProfileName: TLabel;
    edProfileName: TEdit;
    lblEndpoint: TLabel;
    edEndpoint: TEdit;
    btnConnect: TButton;
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
    procedure btnSignClick(Sender: TObject);
  private
    FProvider: TsgcAzureTrustedSigningProvider;
    procedure Log(const aMsg: string);
  end;

var
  FormMain: TFormMain;

implementation

{$R *.dfm}

procedure TFormMain.FormCreate(Sender: TObject);
begin
  FProvider := nil;
  edEndpoint.Text := 'https://eus.codesigning.azure.net';
  edProfileName.Text := 'default';
  Log('Azure Trusted Signing demo ready. Enter credentials and connect.');
end;

procedure TFormMain.btnConnectClick(Sender: TObject);
begin
  if Trim(edTenantId.Text) = '' then
  begin
    Log('ERROR: Please enter Tenant ID');
    Exit;
  end;

  if Trim(edClientId.Text) = '' then
  begin
    Log('ERROR: Please enter Client ID');
    Exit;
  end;

  if Trim(edClientSecret.Text) = '' then
  begin
    Log('ERROR: Please enter Client Secret');
    Exit;
  end;

  if Trim(edAccountName.Text) = '' then
  begin
    Log('ERROR: Please enter Account Name');
    Exit;
  end;

  Log('Connecting to Azure Trusted Signing...');

  if FProvider <> nil then
    FreeAndNil(FProvider);

  FProvider := TsgcAzureTrustedSigningProvider.Create(nil);
  try
    FProvider.TenantId := edTenantId.Text;
    FProvider.ClientId := edClientId.Text;
    FProvider.ClientSecret := edClientSecret.Text;
    FProvider.AccountName := edAccountName.Text;
    FProvider.CertificateProfileName := edProfileName.Text;
    FProvider.Endpoint := edEndpoint.Text;
    FProvider.Connect;
    Log('SUCCESS: Connected to Azure Trusted Signing');
    Log('Certificate: ' + FProvider.Certificate.Subject);
  except
    on E: Exception do
    begin
      Log('ERROR: ' + E.Message);
      FreeAndNil(FProvider);
    end;
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
    Log('ERROR: Please connect to Azure first');
    Exit;
  end;

  if Trim(memoData.Lines.Text) = '' then
  begin
    Log('ERROR: Please enter data to sign');
    Exit;
  end;

  Log('Signing with Azure Trusted Signing...');

  vSigner := TsgcCAdESSigner.Create(nil);
  try
    try
      vSigner.KeyProvider := FProvider as IsgcKeyProvider;
      vSigner.Level := clBES;
      vSigner.Detached := True;

      vData := TEncoding.UTF8.GetBytes(memoData.Lines.Text);
      vBase64 := vSigner.SignDataBase64(vData);
      memoSignature.Lines.Text := vBase64;

      Log('SUCCESS: Data signed with CAdES-BES using Azure');
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

