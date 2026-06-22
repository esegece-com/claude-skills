# TsgcWindowsCertStoreProvider - Example

Full source of `frmMain.pas` from the **Authenticode** demo, which uses `TsgcWindowsCertStoreProvider`.

API reference: [TsgcWindowsCertStoreProvider](../reference/api/TsgcWindowsCertStoreProvider.md)
Source demo: `Authenticode` (file `frmMain.pas`)

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
  StdCtrls, ExtCtrls, ComCtrls,
  // sgcSign
  sgcSign_Types, sgcSign_Interfaces,
  sgcSign_Authenticode,
  sgcSign_KeyProvider_WinCertStore, sgcSign_KeyProvider_PFX,
  sgcSign_TSA;

type
  TFormMain = class(TForm)
    pnlTop: TPanel;
    lblInput: TLabel;
    edInput: TEdit;
    btnBrowseInput: TButton;
    lblOutput: TLabel;
    edOutput: TEdit;
    btnBrowseOutput: TButton;
    lblHash: TLabel;
    cbHash: TComboBox;
    lblLevel: TLabel;
    cbLevel: TComboBox;
    lblTSA: TLabel;
    edTSA: TEdit;
    lblDescription: TLabel;
    edDescription: TEdit;
    lblURL: TLabel;
    edURL: TEdit;
    chkAppend: TCheckBox;
    pnlProvider: TPanel;
    lblProvider: TLabel;
    cbProvider: TComboBox;
    lblCertFilter: TLabel;
    edCertFilter: TEdit;
    lblPFXFile: TLabel;
    edPFXFile: TEdit;
    btnBrowsePFX: TButton;
    lblPFXPassword: TLabel;
    edPFXPassword: TEdit;
    btnShowCerts: TButton;
    pnlActions: TPanel;
    btnSign: TButton;
    btnVerify: TButton;
    lblLog: TLabel;
    memoLog: TMemo;
    dlgOpenInput: TOpenDialog;
    dlgSaveOutput: TSaveDialog;
    dlgOpenPFX: TOpenDialog;
    procedure FormCreate(Sender: TObject);
    procedure btnBrowseInputClick(Sender: TObject);
    procedure btnBrowseOutputClick(Sender: TObject);
    procedure btnBrowsePFXClick(Sender: TObject);
    procedure btnShowCertsClick(Sender: TObject);
    procedure btnSignClick(Sender: TObject);
    procedure btnVerifyClick(Sender: TObject);
    procedure cbLevelChange(Sender: TObject);
    procedure cbProviderChange(Sender: TObject);
    procedure edInputChange(Sender: TObject);
  private
    procedure Log(const aMsg: string);
    procedure UpdateProviderControls;
    procedure UpdateLevelControls;
    function CreateKeyProvider: IsgcKeyProvider;
    function MapHash: TsgcAuthenticodeHashAlgorithm;
    function MapLevel: TsgcAuthenticodeLevel;
    function BytesToHex(const aBytes: TBytes): string;
  end;

var
  FormMain: TFormMain;

implementation

{$R *.dfm}

const
  CERT_STORE_PROV_SYSTEM_W_DEMO = 10;
  CERT_SYSTEM_STORE_CURRENT_USER_DEMO = $00010000;
  CERT_FIND_ANY_DEMO = 0;
  X509_ASN_ENCODING_DEMO = $00000001;
  PKCS_7_ASN_ENCODING_DEMO = $00010000;
  CERT_NAME_SIMPLE_DISPLAY_TYPE_DEMO = 4;
  CERT_NAME_ISSUER_FLAG_DEMO = $00000001;
  CERT_SHA1_HASH_PROP_ID_DEMO = 3;
  szOID_PKIX_KP_CODE_SIGNING_DEMO = '1.3.6.1.5.5.7.3.3';
  THUMB_PREFIX = 'THUMB:';

type
  HCERTSTORE_DEMO = THandle;
  PCCERT_CONTEXT_DEMO = Pointer;

  TCryptIntegerBlob = record
    cbData: DWORD;
    pbData: PByte;
  end;

  TCryptObjIdBlob = record
    cbData: DWORD;
    pbData: PByte;
  end;

  TCryptAlgorithmIdentifier = record
    pszObjId: PAnsiChar;
    Parameters: TCryptObjIdBlob;
  end;

  TCertNameBlob = record
    cbData: DWORD;
    pbData: PByte;
  end;

  TCryptBitBlob = record
    cbData: DWORD;
    pbData: PByte;
    cUnusedBits: DWORD;
  end;

  TCertPublicKeyInfo = record
    Algorithm: TCryptAlgorithmIdentifier;
    PublicKey: TCryptBitBlob;
  end;

  PCertInfoRec = ^TCertInfoRec;

  TCertInfoRec = record
    dwVersion: DWORD;
    SerialNumber: TCryptIntegerBlob;
    SignatureAlgorithm: TCryptAlgorithmIdentifier;
    Issuer: TCertNameBlob;
    NotBefore: TFileTime;
    NotAfter: TFileTime;
    Subject: TCertNameBlob;
    SubjectPublicKeyInfo: TCertPublicKeyInfo;
    // more fields follow, but we do not need them here
  end;

  PCertContextRec = ^TCertContextRec;

  TCertContextRec = record
    dwCertEncodingType: DWORD;
    pbCertEncoded: PByte;
    cbCertEncoded: DWORD;
    pCertInfo: PCertInfoRec;
    HCERTSTORE: HCERTSTORE_DEMO;
  end;

  PCERT_ENHKEY_USAGE_DEMO = ^CERT_ENHKEY_USAGE_DEMO;

  CERT_ENHKEY_USAGE_DEMO = record
    cUsageIdentifier: DWORD;
    rgpszUsageIdentifier: ^PAnsiChar;
  end;

  TCertInfoDemo = record
    Subject: string;
    Issuer: string;
    Thumbprint: string;
    NotBefore: TDateTime;
    NotAfter: TDateTime;
  end;

function CertOpenSystemStoreW_Demo(hprov: THandle;
  szSubsystemProtocol: PWideChar): HCERTSTORE_DEMO; stdcall;
  external 'crypt32.dll' name 'CertOpenSystemStoreW';

function CertEnumCertificatesInStore_Demo(HCERTSTORE: HCERTSTORE_DEMO;
  pPrevCertContext: PCCERT_CONTEXT_DEMO): PCCERT_CONTEXT_DEMO; stdcall;
  external 'crypt32.dll' name 'CertEnumCertificatesInStore';

function CertCloseStore_Demo(HCERTSTORE: HCERTSTORE_DEMO; dwFlags: DWORD): BOOL;
  stdcall; external 'crypt32.dll' name 'CertCloseStore';

function CertFreeCertificateContext_Demo(PCertContext: PCCERT_CONTEXT_DEMO)
  : BOOL; stdcall; external 'crypt32.dll' name 'CertFreeCertificateContext';

function CertGetEnhancedKeyUsage_Demo(PCertContext: PCCERT_CONTEXT_DEMO;
  dwFlags: DWORD; pUsage: PCERT_ENHKEY_USAGE_DEMO; var pcbUsage: DWORD): BOOL;
  stdcall; external 'crypt32.dll' name 'CertGetEnhancedKeyUsage';

function CertGetNameStringW_Demo(PCertContext: PCCERT_CONTEXT_DEMO;
  dwType: DWORD; dwFlags: DWORD; pvTypePara: Pointer; pszNameString: PWideChar;
  cchNameString: DWORD): DWORD; stdcall;
  external 'crypt32.dll' name 'CertGetNameStringW';

function CertGetCertificateContextProperty_Demo(PCertContext
  : PCCERT_CONTEXT_DEMO; dwPropId: DWORD; pvData: Pointer; var pcbData: DWORD)
  : BOOL; stdcall;
  external 'crypt32.dll' name 'CertGetCertificateContextProperty';

function FileTimeToLocalDateTime(const aFT: TFileTime): TDateTime;
var
  vLocal: TFileTime;
  vSys: TSystemTime;
begin
  Result := 0;
  if FileTimeToLocalFileTime(aFT, vLocal) then
    if FileTimeToSystemTime(vLocal, vSys) then
      Result := SystemTimeToDateTime(vSys);
end;

function CertHasCodeSigningEKU_Demo(PCertContext: PCCERT_CONTEXT_DEMO): Boolean;
var
  vSize: DWORD;
  oUsage: PCERT_ENHKEY_USAGE_DEMO;
  vBuf: TBytes;
  vI: Integer;
  pOid: PAnsiChar;
  pArr: ^PAnsiChar;
begin
  Result := False;
  vSize := 0;
  CertGetEnhancedKeyUsage_Demo(PCertContext, 0, nil, vSize);
  if vSize = 0 then
    Exit;
  SetLength(vBuf, vSize);
  oUsage := PCERT_ENHKEY_USAGE_DEMO(@vBuf[0]);
  if not CertGetEnhancedKeyUsage_Demo(PCertContext, 0, oUsage, vSize) then
    Exit;
  // If no EKU extension is present, some implementations treat the cert as
  // usable for any purpose. We explicitly require the code-signing OID.
  if oUsage^.cUsageIdentifier = 0 then
    Exit;
  pArr := Pointer(oUsage^.rgpszUsageIdentifier);
  for vI := 0 to Integer(oUsage^.cUsageIdentifier) - 1 do
  begin
    pOid := PAnsiChar(Pointer(NativeUInt(pArr) + NativeUInt(vI) *
      SizeOf(Pointer))^);
    if string(AnsiString(pOid)) = szOID_PKIX_KP_CODE_SIGNING_DEMO then
    begin
      Result := True;
      Exit;
    end;
  end;
end;

function GetCertThumbprint_Demo(PCertContext: PCCERT_CONTEXT_DEMO): string;
var
  vHash: array [0 .. 63] of Byte;
  vSize: DWORD;
  vI: Integer;
begin
  Result := '';
  vSize := SizeOf(vHash);
  if CertGetCertificateContextProperty_Demo(PCertContext,
    CERT_SHA1_HASH_PROP_ID_DEMO, @vHash[0], vSize) then
  begin
    for vI := 0 to Integer(vSize) - 1 do
      Result := Result + IntToHex(vHash[vI], 2);
  end;
end;

function GetCertNameString_Demo(PCertContext: PCCERT_CONTEXT_DEMO;
  aFlags: DWORD): string;
var
  vBuf: array [0 .. 511] of WideChar;
  vLen: DWORD;
begin
  Result := '';
  vLen := CertGetNameStringW_Demo(PCertContext,
    CERT_NAME_SIMPLE_DISPLAY_TYPE_DEMO, aFlags, nil, @vBuf[0], 512);
  if vLen > 1 then
    Result := WideCharToString(@vBuf[0]);
end;

function ShowCertSelectionDialog(aOwner: TComponent;
  const aCerts: array of TCertInfoDemo; out aSelected: Integer): Boolean;
var
  oDlg: TForm;
  oLV: TListView;
  oBtnOK, oBtnCancel: TButton;
  oCol: TListColumn;
  oItem: TListItem;
  vI: Integer;
begin
  Result := False;
  aSelected := -1;
  oDlg := TForm.Create(aOwner);
  try
    oDlg.Caption := 'Select Code-Signing Certificate';
    oDlg.BorderStyle := bsSizeable;
    oDlg.Position := poMainFormCenter;
    oDlg.ClientWidth := 900;
    oDlg.ClientHeight := 420;

    oLV := TListView.Create(oDlg);
    oLV.Parent := oDlg;
    oLV.Left := 8;
    oLV.Top := 8;
    oLV.Width := 884;
    oLV.Height := 360;
    oLV.Anchors := [akLeft, akTop, akRight, akBottom];
    oLV.ViewStyle := vsReport;
    oLV.ReadOnly := True;
    oLV.RowSelect := True;
    oLV.HideSelection := False;

    oCol := oLV.Columns.Add;
    oCol.Caption := 'Subject';
    oCol.Width := 240;
    oCol := oLV.Columns.Add;
    oCol.Caption := 'Issuer';
    oCol.Width := 220;
    oCol := oLV.Columns.Add;
    oCol.Caption := 'Thumbprint';
    oCol.Width := 240;
    oCol := oLV.Columns.Add;
    oCol.Caption := 'NotBefore';
    oCol.Width := 90;
    oCol := oLV.Columns.Add;
    oCol.Caption := 'NotAfter';
    oCol.Width := 90;

    for vI := 0 to High(aCerts) do
    begin
      oItem := oLV.Items.Add;
      oItem.Caption := aCerts[vI].Subject;
      oItem.SubItems.Add(aCerts[vI].Issuer);
      oItem.SubItems.Add(aCerts[vI].Thumbprint);
      oItem.SubItems.Add(FormatDateTime('yyyy-mm-dd', aCerts[vI].NotBefore));
      oItem.SubItems.Add(FormatDateTime('yyyy-mm-dd', aCerts[vI].NotAfter));
    end;

    if oLV.Items.Count > 0 then
      oLV.Items[0].Selected := True;

    oBtnOK := TButton.Create(oDlg);
    oBtnOK.Parent := oDlg;
    oBtnOK.Caption := 'OK';
    oBtnOK.Width := 90;
    oBtnOK.Height := 28;
    oBtnOK.Left := 700;
    oBtnOK.Top := 380;
    oBtnOK.Anchors := [akRight, akBottom];
    oBtnOK.ModalResult := mrOk;
    oBtnOK.Default := True;

    oBtnCancel := TButton.Create(oDlg);
    oBtnCancel.Parent := oDlg;
    oBtnCancel.Caption := 'Cancel';
    oBtnCancel.Width := 90;
    oBtnCancel.Height := 28;
    oBtnCancel.Left := 800;
    oBtnCancel.Top := 380;
    oBtnCancel.Anchors := [akRight, akBottom];
    oBtnCancel.ModalResult := mrCancel;
    oBtnCancel.Cancel := True;

    if oDlg.ShowModal = mrOk then
    begin
      if (oLV.Selected <> nil) and (oLV.Selected.Index >= 0) then
      begin
        aSelected := oLV.Selected.Index;
        Result := True;
      end;
    end;
  finally
    oDlg.Free;
  end;
end;

procedure TFormMain.FormCreate(Sender: TObject);
begin
  cbHash.ItemIndex := 1; // SHA-256
  cbLevel.ItemIndex := 1; // T
  cbProvider.ItemIndex := 0; // Windows Cert Store
  edTSA.Text := 'http://timestamp.digicert.com';
  UpdateLevelControls;
  UpdateProviderControls;
  Log('Authenticode demo ready. Select an input PE file and a key provider.');
end;

procedure TFormMain.btnBrowseInputClick(Sender: TObject);
begin
  if dlgOpenInput.Execute then
  begin
    edInput.Text := dlgOpenInput.FileName;
    edInputChange(nil);
  end;
end;

procedure TFormMain.btnBrowseOutputClick(Sender: TObject);
begin
  if dlgSaveOutput.Execute then
    edOutput.Text := dlgSaveOutput.FileName;
end;

procedure TFormMain.btnBrowsePFXClick(Sender: TObject);
begin
  if dlgOpenPFX.Execute then
    edPFXFile.Text := dlgOpenPFX.FileName;
end;

procedure TFormMain.cbLevelChange(Sender: TObject);
begin
  UpdateLevelControls;
end;

procedure TFormMain.cbProviderChange(Sender: TObject);
begin
  UpdateProviderControls;
end;

procedure TFormMain.edInputChange(Sender: TObject);
var
  vIn: string;
begin
  vIn := Trim(edInput.Text);
  if (vIn <> '') and (Trim(edOutput.Text) = '') then
    edOutput.Text := ChangeFileExt(vIn, '') + '_signed' + ExtractFileExt(vIn);
end;

procedure TFormMain.UpdateLevelControls;
var
  vIsT: Boolean;
begin
  vIsT := cbLevel.ItemIndex = 1;
  lblTSA.Visible := vIsT;
  edTSA.Visible := vIsT;
end;

procedure TFormMain.UpdateProviderControls;
var
  vIsPFX: Boolean;
begin
  vIsPFX := cbProvider.ItemIndex = 1;
  lblCertFilter.Visible := not vIsPFX;
  edCertFilter.Visible := not vIsPFX;
  lblPFXFile.Visible := vIsPFX;
  edPFXFile.Visible := vIsPFX;
  btnBrowsePFX.Visible := vIsPFX;
  lblPFXPassword.Visible := vIsPFX;
  edPFXPassword.Visible := vIsPFX;
  btnShowCerts.Enabled := not vIsPFX;
end;

procedure TFormMain.btnShowCertsClick(Sender: TObject);
var
  hStore: HCERTSTORE_DEMO;
  pCert: PCCERT_CONTEXT_DEMO;
  pCtx: PCertContextRec;
  oCerts: array of TCertInfoDemo;
  vInfo: TCertInfoDemo;
  vCount, vSelected: Integer;
begin
  hStore := CertOpenSystemStoreW_Demo(0, 'MY');
  if hStore = 0 then
  begin
    Log('ERROR: Cannot open Windows certificate store');
    MessageDlg('Cannot open Windows certificate store', mtError, [mbOK], 0);
    Exit;
  end;

  vCount := 0;
  SetLength(oCerts, 0);
  try
    pCert := CertEnumCertificatesInStore_Demo(hStore, nil);
    while pCert <> nil do
    begin
      if CertHasCodeSigningEKU_Demo(pCert) then
      begin
        pCtx := PCertContextRec(pCert);
        vInfo.Subject := GetCertNameString_Demo(pCert, 0);
        vInfo.Issuer := GetCertNameString_Demo(pCert,
          CERT_NAME_ISSUER_FLAG_DEMO);
        vInfo.Thumbprint := GetCertThumbprint_Demo(pCert);
        if pCtx^.pCertInfo <> nil then
        begin
          vInfo.NotBefore := FileTimeToLocalDateTime
            (pCtx^.pCertInfo^.NotBefore);
          vInfo.NotAfter := FileTimeToLocalDateTime(pCtx^.pCertInfo^.NotAfter);
        end
        else
        begin
          vInfo.NotBefore := 0;
          vInfo.NotAfter := 0;
        end;
        SetLength(oCerts, vCount + 1);
        oCerts[vCount] := vInfo;
        Inc(vCount);
      end;
      pCert := CertEnumCertificatesInStore_Demo(hStore, pCert);
    end;

    if vCount = 0 then
    begin
      Log('No code-signing certificates found in the current user store');
      MessageDlg('No code-signing certificates found in the current user store',
        mtInformation, [mbOK], 0);
      Exit;
    end;

    if ShowCertSelectionDialog(Self, oCerts, vSelected) then
    begin
      edCertFilter.Text := THUMB_PREFIX + oCerts[vSelected].Thumbprint;
      Log('Selected: ' + oCerts[vSelected].Subject + ' (thumbprint: ' +
        oCerts[vSelected].Thumbprint + ')');
    end;
  finally
    CertCloseStore_Demo(hStore, 0);
  end;
end;

function TFormMain.MapHash: TsgcAuthenticodeHashAlgorithm;
begin
  case cbHash.ItemIndex of
    0:
      Result := ahSHA1;
    1:
      Result := ahSHA256;
    2:
      Result := ahSHA384;
    3:
      Result := ahSHA512;
  else
    Result := ahSHA256;
  end;
end;

function TFormMain.MapLevel: TsgcAuthenticodeLevel;
begin
  if cbLevel.ItemIndex = 1 then
    Result := alT
  else
    Result := alBES;
end;

function TFormMain.CreateKeyProvider: IsgcKeyProvider;
var
  oWin: TsgcWindowsCertStoreProvider;
  oPFX: TsgcPFXKeyProvider;
begin
  Result := nil;
  if cbProvider.ItemIndex = 1 then
  begin
    if Trim(edPFXFile.Text) = '' then
      raise Exception.Create('Please select a PFX file');
    oPFX := TsgcPFXKeyProvider.Create(nil);
    oPFX.FileName := edPFXFile.Text;
    oPFX.Password := edPFXPassword.Text;
    oPFX.LoadFromFile;
    Log('PFX certificate loaded: ' + oPFX.Certificate.Subject);
    Result := oPFX as IsgcKeyProvider;
  end
  else
  begin
    if Trim(edCertFilter.Text) = '' then
      raise Exception.Create('Please enter a certificate filter (CN/subject) ' +
        'or use "Show Code-Signing Certificates"');
    oWin := TsgcWindowsCertStoreProvider.Create(nil);
    if Pos(THUMB_PREFIX, UpperCase(Trim(edCertFilter.Text))) = 1 then
      oWin.SelectCertificateByThumbprint(Copy(Trim(edCertFilter.Text),
        Length(THUMB_PREFIX) + 1, MaxInt))
    else
      oWin.SelectCertificateBySubject(edCertFilter.Text);
    Log('Windows Store certificate loaded: ' + oWin.Certificate.Subject);
    Result := oWin as IsgcKeyProvider;
  end;
end;

function TFormMain.BytesToHex(const aBytes: TBytes): string;
const
  cHex: array [0 .. 15] of Char = '0123456789ABCDEF';
var
  vI: Integer;
  vB: Byte;
begin
  SetLength(Result, Length(aBytes) * 2);
  for vI := 0 to Length(aBytes) - 1 do
  begin
    vB := aBytes[vI];
    Result[vI * 2 + 1] := cHex[vB shr 4];
    Result[vI * 2 + 2] := cHex[vB and $0F];
  end;
end;

procedure TFormMain.btnSignClick(Sender: TObject);
var
  oSigner: TsgcAuthenticodeSigner;
  oTSA: TsgcTSAClient;
  vKey: IsgcKeyProvider;
  vIn, vOut: string;
begin
  vIn := Trim(edInput.Text);
  vOut := Trim(edOutput.Text);
  if vIn = '' then
  begin
    Log('ERROR: Please select an input PE file');
    Exit;
  end;
  if vOut = '' then
  begin
    Log('ERROR: Please specify an output path');
    Exit;
  end;
  if not FileExists(vIn) then
  begin
    Log('ERROR: Input file does not exist: ' + vIn);
    Exit;
  end;

  oSigner := nil;
  oTSA := nil;
  try
    try
      vKey := CreateKeyProvider;

      oSigner := TsgcAuthenticodeSigner.Create(nil);
      oSigner.KeyProvider := vKey;
      oSigner.Hash := MapHash;
      oSigner.Level := MapLevel;
      oSigner.Description := edDescription.Text;
      oSigner.URL := edURL.Text;
      oSigner.AppendSignature := chkAppend.Checked;

      if oSigner.Level = alT then
      begin
        if Trim(edTSA.Text) = '' then
          raise Exception.Create('TSA URL is required for Authenticode-T');
        oTSA := TsgcTSAClient.Create(nil);
        oTSA.URL := edTSA.Text;
        oSigner.TSAClient := oTSA as IsgcTSAClient;
        Log('Using TSA: ' + edTSA.Text);
      end;

      Log('Signing file...');
      oSigner.SignFile(vIn, vOut);
      Log('SUCCESS: Signed file written to ' + vOut);
    except
      on E: Exception do
        Log('ERROR: ' + E.Message);
    end;
  finally
    oSigner.Free;
    oTSA.Free;
    vKey := nil;
  end;
end;

procedure TFormMain.btnVerifyClick(Sender: TObject);
var
  oVerifier: TsgcAuthenticodeVerifier;
  oResult: TsgcAuthenticodeVerifyResult;
  vPath: string;
begin
  vPath := Trim(edOutput.Text);
  if vPath = '' then
    vPath := Trim(edInput.Text);
  if vPath = '' then
  begin
    Log('ERROR: Please specify a file to verify');
    Exit;
  end;
  if not FileExists(vPath) then
  begin
    Log('ERROR: File does not exist: ' + vPath);
    Exit;
  end;

  oVerifier := TsgcAuthenticodeVerifier.Create(nil);
  try
    try
      Log('Verifying: ' + vPath);
      oResult := oVerifier.Verify(vPath);
      if oResult.Valid then
        Log('  Valid       : YES')
      else
        Log('  Valid       : NO (' + oResult.ErrorMessage + ')');
      Log('  Subject     : ' + oResult.SubjectName);
      Log('  Issuer      : ' + oResult.IssuerName);
      Log('  Computed    : ' + BytesToHex(oResult.ComputedHash));
      Log('  Embedded    : ' + BytesToHex(oResult.EmbeddedHash));
      if oResult.HasTimestamp then
        Log('  Timestamp   : present')
      else
        Log('  Timestamp   : none');
    except
      on E: Exception do
        Log('ERROR: ' + E.Message);
    end;
  finally
    oVerifier.Free;
  end;
end;

procedure TFormMain.Log(const aMsg: string);
begin
  memoLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) + ' ' + aMsg);
end;

end.
```

