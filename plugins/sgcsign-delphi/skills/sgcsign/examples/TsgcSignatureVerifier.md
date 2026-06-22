# TsgcSignatureVerifier - Example

Full source of `frmMain.pas` from the **EFactura** demo, which uses `TsgcSignatureVerifier`.

API reference: [TsgcSignatureVerifier](../reference/api/TsgcSignatureVerifier.md)
Source demo: `EFactura` (file `frmMain.pas`)

```pascal
{ ***************************************************************************
  sgcSign component

  written by eSeGeCe
  copyright (c) 2026
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
  sgcSign_DocumentSigner, sgcSign_KeyProvider_WinCertStore,
  sgcSign_KeyProvider_PEM, sgcSign_KeyProvider_PFX,
  sgcSign_Verifier;

type
  TFormMain = class(TForm)
    memoXML: TMemo;
    memoResult: TMemo;
    memoLog: TMemo;
    btnSign: TButton;
    btnVerify: TButton;
    btnListCerts: TButton;
    edCertFilter: TEdit;
    lblCertFilter: TLabel;
    lblSourceXML: TLabel;
    lblSignedXML: TLabel;
    lblLog: TLabel;
    pnlTop: TPanel;
    pnlClient: TPanel;
    rgCertSource: TRadioGroup;
    lblCertFile: TLabel;
    edCertFile: TEdit;
    btnBrowseCert: TButton;
    lblKeyFile: TLabel;
    edKeyFile: TEdit;
    btnBrowseKey: TButton;
    lblKeyPassword: TLabel;
    edKeyPassword: TEdit;
    dlgOpen: TOpenDialog;
    procedure btnSignClick(Sender: TObject);
    procedure btnVerifyClick(Sender: TObject);
    procedure btnListCertsClick(Sender: TObject);
    procedure FormCreate(Sender: TObject);
    procedure rgCertSourceClick(Sender: TObject);
    procedure btnBrowseCertClick(Sender: TObject);
    procedure btnBrowseKeyClick(Sender: TObject);
    procedure edCertFileChange(Sender: TObject);
  private
    procedure Log(const aMsg: string);
    function IsPFXExt(const aFileName: string): Boolean;
    procedure UpdateCertSourceUI;
  end;

var
  FormMain: TFormMain;

implementation

{$R *.dfm}

procedure TFormMain.FormCreate(Sender: TObject);
begin
  memoXML.Lines.Text := '<?xml version="1.0" encoding="UTF-8"?>' + sLineBreak +
    '<Invoice xmlns="urn:oasis:names:specification:ubl:schema:xsd:Invoice-2"' +
    sLineBreak +
    '  xmlns:cbc="urn:oasis:names:specification:ubl:schema:xsd:CommonBasicComponents-2"'
    + sLineBreak +
    '  xmlns:cac="urn:oasis:names:specification:ubl:schema:xsd:CommonAggregateComponents-2">'
    + sLineBreak + '  <cbc:ID>RO-2026-001</cbc:ID>' + sLineBreak +
    '  <cbc:IssueDate>2026-03-08</cbc:IssueDate>' + sLineBreak +
    '  <cbc:InvoiceTypeCode>380</cbc:InvoiceTypeCode>' + sLineBreak +
    '  <cbc:DocumentCurrencyCode>RON</cbc:DocumentCurrencyCode>' + sLineBreak +
    '  <cac:AccountingSupplierParty>' + sLineBreak + '    <cac:Party>' +
    sLineBreak +
    '      <cac:PartyName><cbc:Name>Firma Demo SRL</cbc:Name></cac:PartyName>' +
    sLineBreak + '      <cac:PartyTaxScheme>' + sLineBreak +
    '        <cbc:CompanyID>RO12345678</cbc:CompanyID>' + sLineBreak +
    '        <cac:TaxScheme><cbc:ID>VAT</cbc:ID></cac:TaxScheme>' + sLineBreak +
    '      </cac:PartyTaxScheme>' + sLineBreak + '    </cac:Party>' + sLineBreak
    + '  </cac:AccountingSupplierParty>' + sLineBreak +
    '  <cac:LegalMonetaryTotal>' + sLineBreak +
    '    <cbc:TaxExclusiveAmount currencyID="RON">1000.00</cbc:TaxExclusiveAmount>'
    + sLineBreak +
    '    <cbc:TaxInclusiveAmount currencyID="RON">1190.00</cbc:TaxInclusiveAmount>'
    + sLineBreak +
    '    <cbc:PayableAmount currencyID="RON">1190.00</cbc:PayableAmount>' +
    sLineBreak + '  </cac:LegalMonetaryTotal>' + sLineBreak + '</Invoice>';
  UpdateCertSourceUI;
  Log('e-Factura demo ready. Choose certificate source and click Sign.');
end;

function TFormMain.IsPFXExt(const aFileName: string): Boolean;
var
  vExt: string;
begin
  vExt := LowerCase(ExtractFileExt(aFileName));
  Result := (vExt = '.pfx') or (vExt = '.p12');
end;

procedure TFormMain.UpdateCertSourceUI;
var
  vStore: Boolean;
  vKeyEnabled: Boolean;
begin
  vStore := rgCertSource.ItemIndex = 0;

  lblCertFilter.Visible := vStore;
  edCertFilter.Visible := vStore;
  btnListCerts.Visible := vStore;

  lblCertFile.Visible := not vStore;
  edCertFile.Visible := not vStore;
  btnBrowseCert.Visible := not vStore;
  lblKeyFile.Visible := not vStore;
  edKeyFile.Visible := not vStore;
  btnBrowseKey.Visible := not vStore;
  lblKeyPassword.Visible := not vStore;
  edKeyPassword.Visible := not vStore;

  if not vStore then
  begin
    vKeyEnabled := not IsPFXExt(edCertFile.Text);
    lblKeyFile.Enabled := vKeyEnabled;
    edKeyFile.Enabled := vKeyEnabled;
    btnBrowseKey.Enabled := vKeyEnabled;
  end;
end;

procedure TFormMain.rgCertSourceClick(Sender: TObject);
begin
  UpdateCertSourceUI;
end;

procedure TFormMain.edCertFileChange(Sender: TObject);
begin
  UpdateCertSourceUI;
end;

procedure TFormMain.btnBrowseCertClick(Sender: TObject);
begin
  dlgOpen.Filter := 'Certificate / Bundle (*.pem;*.crt;*.cer;*.pfx;*.p12)|' +
    '*.pem;*.crt;*.cer;*.pfx;*.p12|All files (*.*)|*.*';
  dlgOpen.FileName := edCertFile.Text;
  if dlgOpen.Execute then
    edCertFile.Text := dlgOpen.FileName;
end;

procedure TFormMain.btnBrowseKeyClick(Sender: TObject);
begin
  dlgOpen.Filter := 'PEM key (*.pem;*.key)|*.pem;*.key|All files (*.*)|*.*';
  dlgOpen.FileName := edKeyFile.Text;
  if dlgOpen.Execute then
    edKeyFile.Text := dlgOpen.FileName;
end;

procedure TFormMain.btnSignClick(Sender: TObject);
var
  vSigner: TsgcDocumentSigner;
  vKeyProvider: TComponent;
  vSignedXML: string;
  vCertFile: string;
  vKeyFile: string;
  vUsePFX: Boolean;
  oWin: TsgcWindowsCertStoreProvider;
  oPFX: TsgcPFXKeyProvider;
  oPEM: TsgcPEMKeyProvider;
begin
  if rgCertSource.ItemIndex = 0 then
  begin
    if Trim(edCertFilter.Text) = '' then
    begin
      Log('ERROR: Please enter a certificate filter');
      Exit;
    end;
    oWin := TsgcWindowsCertStoreProvider.Create(nil);
    oWin.SelectCertificateBySubject(edCertFilter.Text);
    vKeyProvider := oWin;
  end
  else
  begin
    vCertFile := Trim(edCertFile.Text);
    if vCertFile = '' then
    begin
      Log('ERROR: Please select a certificate file');
      Exit;
    end;
    if not FileExists(vCertFile) then
    begin
      Log('ERROR: Certificate file not found: ' + vCertFile);
      Exit;
    end;
    vUsePFX := IsPFXExt(vCertFile);
    if vUsePFX then
    begin
      oPFX := TsgcPFXKeyProvider.Create(nil);
      oPFX.FileName := vCertFile;
      oPFX.Password := edKeyPassword.Text;
      vKeyProvider := oPFX;
    end
    else
    begin
      vKeyFile := Trim(edKeyFile.Text);
      if vKeyFile = '' then
      begin
        Log('ERROR: Please select a private key file');
        Exit;
      end;
      if not FileExists(vKeyFile) then
      begin
        Log('ERROR: Private key file not found: ' + vKeyFile);
        Exit;
      end;
      oPEM := TsgcPEMKeyProvider.Create(nil);
      oPEM.CertificateFile := vCertFile;
      oPEM.PrivateKeyFile := vKeyFile;
      oPEM.PrivateKeyPassword := edKeyPassword.Text;
      vKeyProvider := oPEM;
    end;
  end;

  Log('Signing XML with e-Factura profile...');

  vSigner := TsgcDocumentSigner.Create(nil);
  try
    try
      if vKeyProvider is TsgcPFXKeyProvider then
      begin
        TsgcPFXKeyProvider(vKeyProvider).LoadFromFile;
        Log('Certificate loaded (PFX): ' + TsgcPFXKeyProvider(vKeyProvider)
          .Certificate.Subject);
      end
      else if vKeyProvider is TsgcPEMKeyProvider then
      begin
        TsgcPEMKeyProvider(vKeyProvider).LoadFromFile;
        Log('Certificate loaded (PEM): ' + TsgcPEMKeyProvider(vKeyProvider)
          .Certificate.Subject);
      end
      else if vKeyProvider is TsgcWindowsCertStoreProvider then
        Log('Certificate found: ' + TsgcWindowsCertStoreProvider(vKeyProvider)
          .Certificate.Subject);

      vSigner.KeyProvider := vKeyProvider as IsgcKeyProvider;
      vSigner.Profile := spEFactura;
      vSignedXML := vSigner.SignXML(memoXML.Lines.Text);

      memoResult.Lines.Text := vSignedXML;
      Log('SUCCESS: XML signed with e-Factura profile');
      Log('Signed XML length: ' + IntToStr(Length(vSignedXML)) + ' bytes');
    except
      on E: Exception do
        Log('ERROR: ' + E.Message);
    end;
  finally
    vSigner.Free;
    vKeyProvider.Free;
  end;
end;

procedure TFormMain.btnVerifyClick(Sender: TObject);
var
  vVerifier: TsgcSignatureVerifier;
  vStatus: TsgcVerificationStatus;
begin
  if Trim(memoResult.Lines.Text) = '' then
  begin
    Log('ERROR: No signed XML to verify. Sign first.');
    Exit;
  end;

  Log('Verifying signature...');

  vVerifier := TsgcSignatureVerifier.Create(nil);
  try
    vStatus := vVerifier.Verify(memoResult.Lines.Text);
    case vStatus of
      vsValid:
        Log('VERIFICATION: VALID - Signature is correct');
      vsInvalid:
        Log('VERIFICATION: INVALID - Signature verification failed');
      vsIndeterminate:
        Log('VERIFICATION: INDETERMINATE');
      vsCertificateExpired:
        Log('VERIFICATION: Certificate has expired');
      vsCertificateRevoked:
        Log('VERIFICATION: Certificate has been revoked');
      vsTimestampInvalid:
        Log('VERIFICATION: Timestamp is invalid');
    end;
    Log(vVerifier.GetVerificationDetails);
  except
    on E: Exception do
      Log('VERIFY ERROR: ' + E.Message);
  end;
  vVerifier.Free;
end;

procedure TFormMain.btnListCertsClick(Sender: TObject);
var
  vProvider: TsgcWindowsCertStoreProvider;
  vCerts: TStringList;
  I: Integer;
begin
  Log('Listing certificates from Windows Certificate Store (MY)...');

  vProvider := TsgcWindowsCertStoreProvider.Create(nil);
  try
    vCerts := vProvider.EnumerateCertificates;
    try
      if vCerts.Count = 0 then
        Log('No certificates found in store.')
      else
      begin
        Log('Found ' + IntToStr(vCerts.Count) + ' certificates:');
        for I := 0 to vCerts.Count - 1 do
          Log('  [' + IntToStr(I + 1) + '] ' + vCerts[I]);
      end;
    finally
      vCerts.Free;
    end;
  except
    on E: Exception do
      Log('ERROR: ' + E.Message);
  end;
  vProvider.Free;
end;

procedure TFormMain.Log(const aMsg: string);
begin
  memoLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) + ' ' + aMsg);
end;

end.
```

