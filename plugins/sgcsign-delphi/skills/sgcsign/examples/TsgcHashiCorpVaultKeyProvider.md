# TsgcHashiCorpVaultKeyProvider - Example

Full source of `frmMain.pas` from the **KeyProvider_Vault** demo, which uses `TsgcHashiCorpVaultKeyProvider`.

API reference: [TsgcHashiCorpVaultKeyProvider](../reference/api/TsgcHashiCorpVaultKeyProvider.md)
Source demo: `KeyProvider_Vault` (file `frmMain.pas`)

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
  sgcSign_CAdES, sgcSign_KeyProvider_Vault;

type
  TFormMain = class(TForm)
    pnlTop: TPanel;
    lblAddress: TLabel;
    edAddress: TEdit;
    lblToken: TLabel;
    edToken: TEdit;
    lblMountPath: TLabel;
    edMountPath: TEdit;
    lblKeyName: TLabel;
    edKeyName: TEdit;
    lblCertFile: TLabel;
    edCertFile: TEdit;
    btnBrowseCert: TButton;
    btnConnect: TButton;
    pnlClient: TPanel;
    lblData: TLabel;
    memoData: TMemo;
    lblSignature: TLabel;
    memoSignature: TMemo;
    btnSign: TButton;
    lblLog: TLabel;
    memoLog: TMemo;
    dlgOpen: TOpenDialog;
    procedure FormCreate(Sender: TObject);
    procedure btnBrowseCertClick(Sender: TObject);
    procedure btnConnectClick(Sender: TObject);
    procedure btnSignClick(Sender: TObject);
  private
    FProvider: TsgcHashiCorpVaultKeyProvider;
    procedure Log(const aMsg: string);
  end;

var
  FormMain: TFormMain;

implementation

{$R *.dfm}

procedure TFormMain.FormCreate(Sender: TObject);
begin
  FProvider := nil;
  edAddress.Text := 'https://127.0.0.1:8200';
  edMountPath.Text := 'transit';
  Log('HashiCorp Vault demo ready. Enter Vault details and connect.');
  Log('Note: Vault Transit does not store certificates. Provide one externally.');
end;

procedure TFormMain.btnBrowseCertClick(Sender: TObject);
begin
  dlgOpen.Filter :=
    'Certificate Files (*.der;*.cer;*.crt;*.pem)|*.der;*.cer;*.crt;*.pem|All Files (*.*)|*.*';
  if dlgOpen.Execute then
    edCertFile.Text := dlgOpen.FileName;
end;

procedure TFormMain.btnConnectClick(Sender: TObject);
begin
  if Trim(edAddress.Text) = '' then
  begin
    Log('ERROR: Please enter Vault address');
    Exit;
  end;

  if Trim(edToken.Text) = '' then
  begin
    Log('ERROR: Please enter Vault token');
    Exit;
  end;

  if Trim(edKeyName.Text) = '' then
  begin
    Log('ERROR: Please enter transit key name');
    Exit;
  end;

  if Trim(edCertFile.Text) = '' then
  begin
    Log('ERROR: Please select a certificate file (required for Vault Transit)');
    Exit;
  end;

  Log('Connecting to HashiCorp Vault...');

  if FProvider <> nil then
    FreeAndNil(FProvider);

  FProvider := TsgcHashiCorpVaultKeyProvider.Create(nil);
  try
    FProvider.VaultAddress := edAddress.Text;
    FProvider.Token := edToken.Text;
    FProvider.MountPath := edMountPath.Text;
    FProvider.KeyName := edKeyName.Text;
    FProvider.SetCertificateFromFile(edCertFile.Text);
    FProvider.Connect;
    Log('SUCCESS: Connected to Vault Transit');
    Log('Certificate: ' + FProvider.ExternalCertificate.Subject);
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
    Log('ERROR: Please connect to Vault first');
    Exit;
  end;

  if Trim(memoData.Lines.Text) = '' then
  begin
    Log('ERROR: Please enter data to sign');
    Exit;
  end;

  Log('Signing with HashiCorp Vault Transit...');

  vSigner := TsgcCAdESSigner.Create(nil);
  try
    try
      vSigner.KeyProvider := FProvider as IsgcKeyProvider;
      vSigner.Level := clBES;
      vSigner.Detached := True;

      vData := TEncoding.UTF8.GetBytes(memoData.Lines.Text);
      vBase64 := vSigner.SignDataBase64(vData);
      memoSignature.Lines.Text := vBase64;

      Log('SUCCESS: Data signed with CAdES-BES using Vault Transit');
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

