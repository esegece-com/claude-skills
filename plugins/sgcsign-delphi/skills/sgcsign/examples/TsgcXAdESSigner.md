# TsgcXAdESSigner - Example

Full source of `frmMain.pas` from the **EU_Employment** demo, which uses `TsgcXAdESSigner`.

API reference: [TsgcXAdESSigner](../reference/api/TsgcXAdESSigner.md)
Source demo: `EU_Employment` (file `frmMain.pas`)

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
  Windows, Messages, SysUtils, Variants, Classes,
  Graphics, Controls, Forms, Dialogs, FileCtrl,
  StdCtrls, ExtCtrls, ComCtrls, Mask,
  // sgcSign
  sgcSign_Types, sgcSign_Interfaces, sgcSign_Classes,
  sgcSign_KeyProvider_PEM, sgcSign_KeyProvider_PFX,
  sgcSign_KeyProvider_WinCertStore, sgcSign_KeyProvider_CSC,
  sgcSign_XAdES, sgcSign_ASiC, sgcSign_Verifier, sgcSign_TrustList;

type
  TsgcLastSignedKind = (lskNone, lskXML, lskASiCS, lskASiCE);

  TFormMain = class(TForm)
    pcMain: TPageControl;
    tsSign: TTabSheet;
    tsVerify: TTabSheet;
    tsReport: TTabSheet;
    tsTrustList: TTabSheet;
    sbMain: TStatusBar;
    dlgOpen: TOpenDialog;
    dlgSave: TSaveDialog;
    // Sign tab - provider
    gbProvider: TGroupBox;
    rgProviderType: TRadioGroup;
    lblCertFile: TLabel;
    edCertFile: TEdit;
    btnBrowseCert: TButton;
    lblKeyFile: TLabel;
    edKeyFile: TEdit;
    btnBrowseKey: TButton;
    lblPFXFile: TLabel;
    edPFXFile: TEdit;
    btnBrowsePFX: TButton;
    lblPassword: TLabel;
    edPassword: TEdit;
    lblWinStore: TLabel;
    edWinStoreFilter: TEdit;
    lblCSCBase: TLabel;
    edCSCBaseURL: TEdit;
    lblCSCUser: TLabel;
    edCSCUser: TEdit;
    edCSCPwd: TEdit;
    lblCSCCred: TLabel;
    edCSCCredID: TEdit;
    lblCSCPin: TLabel;
    edCSCPin: TEdit;
    // Sign tab - country / container
    gbCountry: TGroupBox;
    lblCountry: TLabel;
    cbCountry: TComboBox;
    lblContainer: TLabel;
    cbContainer: TComboBox;
    lblProfile: TLabel;
    // Sign tab - contract details
    gbContract: TGroupBox;
    lblEmployer: TLabel;
    edEmployer: TEdit;
    lblEmployerNIP: TLabel;
    edEmployerNIP: TEdit;
    lblEmployee: TLabel;
    edEmployee: TEdit;
    lblEmployeeID: TLabel;
    edEmployeeID: TEdit;
    lblPosition: TLabel;
    edPosition: TEdit;
    lblStartDate: TLabel;
    edStartDate: TEdit;
    lblSalary: TLabel;
    edSalary: TEdit;
    lblLocation: TLabel;
    edLocation: TEdit;
    btnLoadTemplate: TButton;
    // Sign tab - XML
    gbXML: TGroupBox;
    memoSource: TMemo;
    pnlSignBar: TPanel;
    btnSign: TButton;
    btnSaveOutput: TButton;
    // Verify tab
    lblVerifyInput: TLabel;
    memoVerifyInput: TMemo;
    pnlVerifyBar: TPanel;
    btnLoadSigned: TButton;
    btnUseLast: TButton;
    btnVerify: TButton;
    btnVerifyLTV: TButton;
    lblVerifyResult: TLabel;
    memoVerifyResult: TMemo;
    // Report tab
    lblReport: TLabel;
    memoEtsiReport: TMemo;
    btnSaveReport: TButton;
    // Trust list tab
    gbTrustList: TGroupBox;
    lblCacheDir: TLabel;
    edTrustListCacheDir: TEdit;
    btnBrowseCacheDir: TButton;
    btnRefreshTL: TButton;
    lblTLStatus: TLabel;
    lvServices: TListView;
    gbLookup: TGroupBox;
    lblLookupCert: TLabel;
    edLookupCertFile: TEdit;
    btnBrowseLookupCert: TButton;
    btnLookup: TButton;
    lblLookupResult: TLabel;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure pcMainChange(Sender: TObject);
    procedure rgProviderTypeClick(Sender: TObject);
    procedure btnBrowseCertClick(Sender: TObject);
    procedure btnBrowseKeyClick(Sender: TObject);
    procedure btnBrowsePFXClick(Sender: TObject);
    procedure cbCountryChange(Sender: TObject);
    procedure cbContainerChange(Sender: TObject);
    procedure btnLoadTemplateClick(Sender: TObject);
    procedure btnSignClick(Sender: TObject);
    procedure btnSaveOutputClick(Sender: TObject);
    procedure btnLoadSignedClick(Sender: TObject);
    procedure btnUseLastClick(Sender: TObject);
    procedure btnVerifyClick(Sender: TObject);
    procedure btnVerifyLTVClick(Sender: TObject);
    procedure btnSaveReportClick(Sender: TObject);
    procedure btnRefreshTLClick(Sender: TObject);
    procedure btnBrowseCacheDirClick(Sender: TObject);
    procedure btnBrowseLookupCertClick(Sender: TObject);
    procedure btnLookupClick(Sender: TObject);
  private
    FLastSignedBytes: TBytes;
    FLastSignedKind: TsgcLastSignedKind;
    FLastSignedXML: string;
    FLastReport: string;
    FTrustList: TsgcEUTrustList;
    procedure UpdateProviderControls;
    procedure UpdateProfileLabel;
    function CountryToProfile(aIdx: Integer): TsgcSignatureProfile;
    function CountryISOCode(aIdx: Integer): string;
    function MakeKeyProvider(out aOwned: TComponent): IsgcKeyProvider;
    function BuildContractXML: string;
    function StatusName(aStatus: TsgcVerificationStatus): string;
    function TrustStatusName(aStatus: TsgcTrustServiceStatus): string;
    function DistinctCountriesCount(const aServices
      : TsgcTrustServiceArray): Integer;
    function ExtractInnerSignatureXML(const aSignedBytes: TBytes;
      out aSigned: string): Boolean;
    procedure SetStatus(const aText: string);
    procedure UpdateProfileSnapshot;
    procedure Log(const aMsg: string);
    function XmlEscape(const aText: string): string;
    function TempPath: string;
    function ReadFileAsBytes(const aFileName: string): TBytes;
    function WriteBytesToFile(const aFileName: string;
      const aBytes: TBytes): Boolean;
    function PEMToDER(const aText: string): TBytes;
    function CertFileToDER(const aFileName: string): TBytes;
  end;

var
  FormMain: TFormMain;

implementation

{$R *.dfm}

uses
  StrUtils, sgcSign_Base64;

const
  cAttachmentText = 'These supplementary terms form an integral part of the' +
    ' employment contract. They cover company policies, IT acceptable use' +
    ' and confidentiality obligations.';

  cTrustListDirLeaf = 'sgcSign_TrustList';

  { ----- helpers ------------------------------------------------------------ }

function TFormMain.TempPath: string;
var
  vBuf: array [0 .. MAX_PATH] of Char;
  vLen: DWORD;
begin
  vLen := GetTempPath(Length(vBuf), vBuf);
  if vLen = 0 then
    Result := 'C:\Temp\'
  else
    SetString(Result, vBuf, vLen);
end;

function TFormMain.XmlEscape(const aText: string): string;
var
  vI: Integer;
  vCh: Char;
begin
  Result := '';
  for vI := 1 to Length(aText) do
  begin
    vCh := aText[vI];
    case vCh of
      '&':
        Result := Result + '&amp;';
      '<':
        Result := Result + '&lt;';
      '>':
        Result := Result + '&gt;';
      '"':
        Result := Result + '&quot;';
      '''':
        Result := Result + '&apos;';
    else
      Result := Result + vCh;
    end;
  end;
end;

function TFormMain.ReadFileAsBytes(const aFileName: string): TBytes;
var
  vFS: TFileStream;
begin
  SetLength(Result, 0);
  if not FileExists(aFileName) then
    Exit;
  vFS := TFileStream.Create(aFileName, fmOpenRead or fmShareDenyWrite);
  try
    SetLength(Result, vFS.Size);
    if vFS.Size > 0 then
      vFS.ReadBuffer(Result[0], vFS.Size);
  finally
    vFS.Free;
  end;
end;

function TFormMain.WriteBytesToFile(const aFileName: string;
  const aBytes: TBytes): Boolean;
var
  vFS: TFileStream;
begin
  Result := False;
  try
    vFS := TFileStream.Create(aFileName, fmCreate);
    try
      if Length(aBytes) > 0 then
        vFS.WriteBuffer(aBytes[0], Length(aBytes));
    finally
      vFS.Free;
    end;
    Result := True;
  except
    on E: Exception do
      Log('ERROR writing ' + aFileName + ': ' + E.Message);
  end;
end;

function TFormMain.PEMToDER(const aText: string): TBytes;
var
  vClean, vBody: string;
  vBegin, vEnd: Integer;
  vI: Integer;
  vCh: Char;
begin
  SetLength(Result, 0);
  vBegin := Pos('-----BEGIN', aText);
  if vBegin = 0 then
    Exit;
  vEnd := Pos('-----END', aText);
  if vEnd = 0 then
    Exit;
  // skip past "-----BEGIN ... -----"
  vBegin := Pos('-----', Copy(aText, vBegin + 5, MaxInt));
  if vBegin = 0 then
    Exit;
  vBegin := vBegin + 5 + 5; // first 5 = past BEGIN..., second 5 = past dashes
  vBody := Copy(aText, vBegin, vEnd - vBegin);
  vClean := '';
  for vI := 1 to Length(vBody) do
  begin
    vCh := vBody[vI];
    if (vCh <> #13) and (vCh <> #10) and (vCh <> ' ') and (vCh <> #9) then
      vClean := vClean + vCh;
  end;
  try
    Result := TsgcBase64.Decode(vClean);
  except
    SetLength(Result, 0);
  end;
end;

function TFormMain.CertFileToDER(const aFileName: string): TBytes;
var
  vRaw: TBytes;
  vText: AnsiString;
  vIsPEM: Boolean;
  vI: Integer;
begin
  vRaw := ReadFileAsBytes(aFileName);
  if Length(vRaw) = 0 then
  begin
    SetLength(Result, 0);
    Exit;
  end;
  // Sniff: PEM begins with "-----BEGIN"
  vIsPEM := False;
  if Length(vRaw) >= 10 then
  begin
    SetLength(vText, 10);
    for vI := 0 to 9 do
      vText[vI + 1] := AnsiChar(vRaw[vI]);
    vIsPEM := (vText = '-----BEGIN');
  end;
  if vIsPEM then
  begin
    SetLength(vText, Length(vRaw));
    for vI := 0 to Length(vRaw) - 1 do
      vText[vI + 1] := AnsiChar(vRaw[vI]);
    Result := PEMToDER(string(vText));
  end
  else
    Result := vRaw;
end;

{ ----- form events -------------------------------------------------------- }

procedure TFormMain.FormCreate(Sender: TObject);
begin
  FLastSignedKind := lskNone;
  SetLength(FLastSignedBytes, 0);
  FLastSignedXML := '';
  FLastReport := '';
  FTrustList := nil;

  cbCountry.ItemIndex := 0;
  cbContainer.ItemIndex := 0;
  rgProviderType.ItemIndex := 0;

  edEmployer.Text := 'ACME GmbH';
  edEmployerNIP.Text := 'VATPL-1234567890';
  edEmployee.Text := 'Anna Schmidt';
  edEmployeeID.Text := 'PNOPL-12345678901';
  edPosition.Text := 'Senior Software Engineer';
  edStartDate.Text := FormatDateTime('yyyy-mm-dd', Now);
  edSalary.Text := '4500.00';
  edLocation.Text := 'Berlin, DE';

  edCertFile.Text := 'C:\software\ai\sgcSign\test_certs\test_vatpl.crt';
  edKeyFile.Text := 'C:\software\ai\sgcSign\test_certs\test_vatpl.key';
  edPFXFile.Text := 'C:\software\ai\sgcSign\test_certs\test.p12';
  edWinStoreFilter.Text := '';
  edCSCBaseURL.Text := 'https://csc-sandbox.example/csc/v2';
  edCSCUser.Text := '';
  edCSCPwd.Text := '';
  edCSCCredID.Text := '';
  edCSCPin.Text := '';

  edTrustListCacheDir.Text := IncludeTrailingPathDelimiter(TempPath) +
    cTrustListDirLeaf;

  UpdateProviderControls;
  UpdateProfileLabel;
  UpdateProfileSnapshot;
  Log('Demo ready. Pick a provider, country, container, and click Sign.');
end;

procedure TFormMain.FormDestroy(Sender: TObject);
begin
  if FTrustList <> nil then
  begin
    FTrustList.Free;
    FTrustList := nil;
  end;
end;

procedure TFormMain.pcMainChange(Sender: TObject);
begin
  UpdateProfileSnapshot;
end;

procedure TFormMain.SetStatus(const aText: string);
begin
  if Assigned(sbMain) then
    sbMain.Panels[0].Text := aText;
end;

procedure TFormMain.Log(const aMsg: string);
begin
  SetStatus(FormatDateTime('hh:nn:ss', Now) + '  ' + aMsg);
end;

procedure TFormMain.UpdateProviderControls;
var
  vIdx: Integer;
  vIsPEM, vIsPFX, vIsWin, vIsCSC: Boolean;
begin
  vIdx := rgProviderType.ItemIndex;
  vIsPEM := (vIdx = 0);
  vIsPFX := (vIdx = 1);
  vIsWin := (vIdx = 2);
  vIsCSC := (vIdx = 3);

  edCertFile.Enabled := vIsPEM;
  btnBrowseCert.Enabled := vIsPEM;
  edKeyFile.Enabled := vIsPEM;
  btnBrowseKey.Enabled := vIsPEM;
  edPFXFile.Enabled := vIsPFX;
  btnBrowsePFX.Enabled := vIsPFX;
  edPassword.Enabled := vIsPEM or vIsPFX;
  edWinStoreFilter.Enabled := vIsWin;
  edCSCBaseURL.Enabled := vIsCSC;
  edCSCUser.Enabled := vIsCSC;
  edCSCPwd.Enabled := vIsCSC;
  edCSCCredID.Enabled := vIsCSC;
  edCSCPin.Enabled := vIsCSC;
end;

procedure TFormMain.rgProviderTypeClick(Sender: TObject);
begin
  UpdateProviderControls;
end;

function TFormMain.CountryToProfile(aIdx: Integer): TsgcSignatureProfile;
begin
  case aIdx of
    0:
      Result := spEmploymentDE;
    1:
      Result := spEmploymentIT;
    2:
      Result := spEmploymentES;
    3:
      Result := spEmploymentFR;
    4:
      Result := spEmploymentPL;
    5:
      Result := spEmploymentAT;
    6:
      Result := spEmploymentBE;
    7:
      Result := spEmploymentPT;
    8:
      Result := spEmploymentNL;
  else
    Result := spEmploymentDE;
  end;
end;

function TFormMain.CountryISOCode(aIdx: Integer): string;
begin
  case aIdx of
    0:
      Result := 'DE';
    1:
      Result := 'IT';
    2:
      Result := 'ES';
    3:
      Result := 'FR';
    4:
      Result := 'PL';
    5:
      Result := 'AT';
    6:
      Result := 'BE';
    7:
      Result := 'PT';
    8:
      Result := 'NL';
  else
    Result := 'DE';
  end;
end;

procedure TFormMain.UpdateProfileLabel;
var
  vCfg: TsgcSignProfileConfig;
  vLevel, vHash, vC14N, vTS, vOCSP: string;
  vProfileName: string;
begin
  vCfg := TsgcSignProfileConfig.Create;
  try
    vCfg.LoadProfile(CountryToProfile(cbCountry.ItemIndex));
    case vCfg.SignatureLevel of
      slBB:
        vLevel := 'B-B';
      slBT:
        vLevel := 'B-T';
      slBLT:
        vLevel := 'B-LT';
      slBLTA:
        vLevel := 'B-LTA';
    else
      vLevel := '?';
    end;
    case vCfg.HashAlgorithm of
      haSHA1:
        vHash := 'SHA-1';
      haSHA256:
        vHash := 'SHA-256';
      haSHA384:
        vHash := 'SHA-384';
      haSHA512:
        vHash := 'SHA-512';
    else
      vHash := '?';
    end;
    case vCfg.C14NMethod of
      cmC14N10:
        vC14N := 'inclusive (C14N 1.0)';
      cmC14N10WithComments:
        vC14N := 'inclusive +comments';
      cmExcC14N:
        vC14N := 'exclusive';
      cmExcC14NWithComments:
        vC14N := 'exclusive +comments';
    else
      vC14N := '?';
    end;
    if vCfg.IncludeTimestamp then
      vTS := 'yes'
    else
      vTS := 'no';
    if vCfg.IncludeOCSP then
      vOCSP := 'yes'
    else
      vOCSP := 'no';
    case CountryToProfile(cbCountry.ItemIndex) of
      spEmploymentDE:
        vProfileName := 'spEmploymentDE';
      spEmploymentIT:
        vProfileName := 'spEmploymentIT';
      spEmploymentES:
        vProfileName := 'spEmploymentES';
      spEmploymentFR:
        vProfileName := 'spEmploymentFR';
      spEmploymentPL:
        vProfileName := 'spEmploymentPL';
      spEmploymentAT:
        vProfileName := 'spEmploymentAT';
      spEmploymentBE:
        vProfileName := 'spEmploymentBE';
      spEmploymentPT:
        vProfileName := 'spEmploymentPT';
      spEmploymentNL:
        vProfileName := 'spEmploymentNL';
    else
      vProfileName := '?';
    end;
    lblProfile.Caption := 'Profile: ' + vProfileName + ' | Level: ' + vLevel +
      ' | Hash: ' + vHash + ' | C14N: ' + vC14N + ' | TS: ' + vTS +
      ' | OCSP: ' + vOCSP;
  finally
    vCfg.Free;
  end;
end;

procedure TFormMain.UpdateProfileSnapshot;
var
  vCfg: TsgcSignProfileConfig;
  vSnap: string;
begin
  vCfg := TsgcSignProfileConfig.Create;
  try
    vCfg.LoadProfile(CountryToProfile(cbCountry.ItemIndex));
    vSnap := CountryISOCode(cbCountry.ItemIndex);
    case vCfg.SignatureLevel of
      slBB:
        vSnap := vSnap + ' B-B';
      slBT:
        vSnap := vSnap + ' B-T';
      slBLT:
        vSnap := vSnap + ' B-LT';
      slBLTA:
        vSnap := vSnap + ' B-LTA';
    end;
    if vCfg.IncludeTimestamp then
      vSnap := vSnap + ' +TS';
    if vCfg.IncludeOCSP then
      vSnap := vSnap + ' +OCSP';
  finally
    vCfg.Free;
  end;
  if Assigned(sbMain) then
    sbMain.Panels[1].Text := vSnap;
end;

procedure TFormMain.cbCountryChange(Sender: TObject);
begin
  UpdateProfileLabel;
  UpdateProfileSnapshot;
end;

procedure TFormMain.cbContainerChange(Sender: TObject);
begin
  UpdateProfileLabel;
end;

procedure TFormMain.btnBrowseCertClick(Sender: TObject);
begin
  dlgOpen.Filter := 'PEM (*.pem;*.crt;*.cer)|*.pem;*.crt;*.cer|' +
    'All files (*.*)|*.*';
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

procedure TFormMain.btnBrowsePFXClick(Sender: TObject);
begin
  dlgOpen.Filter := 'PFX/P12 (*.pfx;*.p12)|*.pfx;*.p12|All files (*.*)|*.*';
  dlgOpen.FileName := edPFXFile.Text;
  if dlgOpen.Execute then
    edPFXFile.Text := dlgOpen.FileName;
end;

procedure TFormMain.btnBrowseCacheDirClick(Sender: TObject);
var
  vDir: string;
begin
  vDir := edTrustListCacheDir.Text;
  if SelectDirectory('Select cache directory', '', vDir{$IFDEF UNICODE},
    [sdNewFolder, sdShowEdit, sdValidateDir]{$ENDIF}) then
    edTrustListCacheDir.Text := vDir;
end;

procedure TFormMain.btnBrowseLookupCertClick(Sender: TObject);
begin
  dlgOpen.Filter := 'Certificate (*.crt;*.cer;*.pem)|*.crt;*.cer;*.pem|' +
    'All files (*.*)|*.*';
  dlgOpen.FileName := edLookupCertFile.Text;
  if dlgOpen.Execute then
    edLookupCertFile.Text := dlgOpen.FileName;
end;

{ ----- contract template -------------------------------------------------- }

function TFormMain.BuildContractXML: string;
var
  vCC: string;
begin
  vCC := CountryISOCode(cbCountry.ItemIndex);
  Result := '<?xml version="1.0" encoding="UTF-8"?>' + sLineBreak +
    '<EmploymentContract xmlns="http://eu.example/employment/v1">' + sLineBreak
    + '  <Country>' + XmlEscape(vCC) + '</Country>' + sLineBreak +
    '  <Employer>' + XmlEscape(edEmployer.Text) + '</Employer>' + sLineBreak +
    '  <EmployerNIP>' + XmlEscape(edEmployerNIP.Text) + '</EmployerNIP>' +
    sLineBreak + '  <Employee>' + XmlEscape(edEmployee.Text) + '</Employee>' +
    sLineBreak + '  <EmployeeID>' + XmlEscape(edEmployeeID.Text) +
    '</EmployeeID>' + sLineBreak + '  <Position>' + XmlEscape(edPosition.Text) +
    '</Position>' + sLineBreak + '  <StartDate>' + XmlEscape(edStartDate.Text) +
    '</StartDate>' + sLineBreak + '  <Salary currency="EUR">' +
    XmlEscape(edSalary.Text) + '</Salary>' + sLineBreak + '  <Location>' +
    XmlEscape(edLocation.Text) + '</Location>' + sLineBreak + '  <IssuedAt>' +
    FormatDateTime('yyyy-mm-dd"T"hh:nn:ss"Z"', Now) + '</IssuedAt>' + sLineBreak
    + '</EmploymentContract>';
end;

procedure TFormMain.btnLoadTemplateClick(Sender: TObject);
begin
  memoSource.Lines.Text := BuildContractXML;
  Log('Loaded contract template for ' + CountryISOCode(cbCountry.ItemIndex) +
    '. Edit if needed and click Sign.');
end;

{ ----- key provider factory ---------------------------------------------- }

function TFormMain.MakeKeyProvider(out aOwned: TComponent): IsgcKeyProvider;
var
  vPEM: TsgcPEMKeyProvider;
  vPFX: TsgcPFXKeyProvider;
  vWin: TsgcWindowsCertStoreProvider;
  vCSC: TsgcCSCKeyProvider;
begin
  Result := nil;
  aOwned := nil;
  case rgProviderType.ItemIndex of
    0:
      begin
        if Trim(edCertFile.Text) = '' then
          raise Exception.Create('Certificate file is required for PEM');
        if Trim(edKeyFile.Text) = '' then
          raise Exception.Create('Private key file is required for PEM');
        vPEM := TsgcPEMKeyProvider.Create(nil);
        try
          vPEM.CertificateFile := Trim(edCertFile.Text);
          vPEM.PrivateKeyFile := Trim(edKeyFile.Text);
          vPEM.PrivateKeyPassword := edPassword.Text;
          vPEM.LoadFromFile;
          aOwned := vPEM;
          Result := vPEM as IsgcKeyProvider;
        except
          vPEM.Free;
          raise;
        end;
      end;
    1:
      begin
        if Trim(edPFXFile.Text) = '' then
          raise Exception.Create('PFX file is required');
        vPFX := TsgcPFXKeyProvider.Create(nil);
        try
          vPFX.FileName := Trim(edPFXFile.Text);
          vPFX.Password := edPassword.Text;
          vPFX.LoadFromFile;
          aOwned := vPFX;
          Result := vPFX as IsgcKeyProvider;
        except
          vPFX.Free;
          raise;
        end;
      end;
    2:
      begin
        vWin := TsgcWindowsCertStoreProvider.Create(nil);
        try
          if Trim(edWinStoreFilter.Text) = '' then
            raise Exception.Create
              ('Subject filter is required for Windows Cert Store');
          vWin.SelectCertificateBySubject(Trim(edWinStoreFilter.Text));
          aOwned := vWin;
          Result := vWin as IsgcKeyProvider;
        except
          vWin.Free;
          raise;
        end;
      end;
    3:
      begin
        vCSC := TsgcCSCKeyProvider.Create(nil);
        try
          vCSC.BaseURL := Trim(edCSCBaseURL.Text);
          vCSC.Username := Trim(edCSCUser.Text);
          vCSC.Password := edCSCPwd.Text;
          vCSC.CredentialID := Trim(edCSCCredID.Text);
          vCSC.PIN := edCSCPin.Text;
          // Best-effort load - if the QTSP requires login first it will throw.
          try
            vCSC.LoadCredentialInfo;
          except
            on E: Exception do
              Log('CSC: ' + E.Message + ' (signing will retry)');
          end;
          aOwned := vCSC;
          Result := vCSC as IsgcKeyProvider;
        except
          vCSC.Free;
          raise;
        end;
      end;
  else
    raise Exception.Create('Unknown provider type');
  end;
end;

{ ----- sign --------------------------------------------------------------- }

procedure TFormMain.btnSignClick(Sender: TObject);
var
  vKp: IsgcKeyProvider;
  vOwned: TComponent;
  vSigner: TsgcXAdESSigner;
  vSourceXML, vSignedXML: string;
  vDocs: TsgcASiCDocumentArray;
  vUTF8: UTF8String;
  vAttachUTF8: UTF8String;
  vIdx: Integer;
  vCC: string;
begin
  if Trim(memoSource.Lines.Text) = '' then
  begin
    Log('Source XML is empty - load template first.');
    Exit;
  end;
  vSourceXML := memoSource.Lines.Text;
  vCC := CountryISOCode(cbCountry.ItemIndex);

  Log('Building key provider...');
  try
    vKp := MakeKeyProvider(vOwned);
  except
    on E: Exception do
    begin
      Log('Provider error: ' + E.Message);
      Exit;
    end;
  end;

  vSigner := TsgcXAdESSigner.Create(nil);
  try
    try
      vSigner.KeyProvider := vKp;
      vSigner.Profile.LoadProfile(CountryToProfile(cbCountry.ItemIndex));
      vSigner.XAdESType := xtEnveloped;
      Log('Signing with ' + vCC + ' employment profile...');
      vSignedXML := vSigner.SignXML(vSourceXML);
      FLastSignedXML := vSignedXML;

      vIdx := cbContainer.ItemIndex;
      case vIdx of
        0:
          begin
            // Plain XAdES
            vUTF8 := UTF8Encode(vSignedXML);
            SetLength(FLastSignedBytes, Length(vUTF8));
            if Length(vUTF8) > 0 then
              Move(vUTF8[1], FLastSignedBytes[0], Length(vUTF8));
            FLastSignedKind := lskXML;
            memoSource.Lines.Text := vSignedXML;
            Log('SUCCESS: signed (plain XAdES, ' + IntToStr(Length(vSignedXML))
              + ' chars).');
          end;
        1:
          begin
            // ASiC-S
            vUTF8 := UTF8Encode(vSourceXML);
            SetLength(vDocs, 1);
            vDocs[0].Name := 'employment_contract.xml';
            SetLength(vDocs[0].Data, Length(vUTF8));
            if Length(vUTF8) > 0 then
              Move(vUTF8[1], vDocs[0].Data[0], Length(vUTF8));
            FLastSignedBytes := TsgcASiCContainer.BuildXAdES(apASiCS, vDocs,
              vSignedXML);
            FLastSignedKind := lskASiCS;
            Log('SUCCESS: signed (ASiC-S, ' + IntToStr(Length(FLastSignedBytes))
              + ' bytes).');
          end;
        2:
          begin
            // ASiC-E with attachment
            vUTF8 := UTF8Encode(vSourceXML);
            vAttachUTF8 := UTF8Encode(cAttachmentText);
            SetLength(vDocs, 2);
            vDocs[0].Name := 'employment_contract.xml';
            SetLength(vDocs[0].Data, Length(vUTF8));
            if Length(vUTF8) > 0 then
              Move(vUTF8[1], vDocs[0].Data[0], Length(vUTF8));
            vDocs[1].Name := 'attachment_terms.txt';
            SetLength(vDocs[1].Data, Length(vAttachUTF8));
            if Length(vAttachUTF8) > 0 then
              Move(vAttachUTF8[1], vDocs[1].Data[0], Length(vAttachUTF8));
            FLastSignedBytes := TsgcASiCContainer.BuildXAdES(apASiCE, vDocs,
              vSignedXML);
            FLastSignedKind := lskASiCE;
            Log('SUCCESS: signed (ASiC-E, ' + IntToStr(Length(FLastSignedBytes))
              + ' bytes, +1 attachment).');
          end;
      end;
    except
      on E: Exception do
        Log('SIGN ERROR: ' + E.Message);
    end;
  finally
    vSigner.Free;
    vKp := nil;
    if vOwned <> nil then
      vOwned.Free;
  end;
end;

procedure TFormMain.btnSaveOutputClick(Sender: TObject);
var
  vDefaultExt, vFilter: string;
begin
  if (FLastSignedKind = lskNone) or (Length(FLastSignedBytes) = 0) then
  begin
    Log('Nothing to save - sign a contract first.');
    Exit;
  end;
  case FLastSignedKind of
    lskXML:
      begin
        vDefaultExt := 'xml';
        vFilter := 'Signed XML (*.xml)|*.xml|All files (*.*)|*.*';
      end;
    lskASiCS:
      begin
        vDefaultExt := 'asics';
        vFilter := 'ASiC-S (*.asics)|*.asics|All files (*.*)|*.*';
      end;
    lskASiCE:
      begin
        vDefaultExt := 'asice';
        vFilter := 'ASiC-E (*.asice)|*.asice|All files (*.*)|*.*';
      end;
  else
    vDefaultExt := 'bin';
    vFilter := 'All files (*.*)|*.*';
  end;
  dlgSave.DefaultExt := vDefaultExt;
  dlgSave.Filter := vFilter;
  dlgSave.FileName := 'employment_' +
    LowerCase(CountryISOCode(cbCountry.ItemIndex)) + '.' + vDefaultExt;
  if dlgSave.Execute then
    if WriteBytesToFile(dlgSave.FileName, FLastSignedBytes) then
      Log('Saved ' + IntToStr(Length(FLastSignedBytes)) + ' bytes to ' +
        dlgSave.FileName);
end;

{ ----- verify ------------------------------------------------------------- }

function TFormMain.ExtractInnerSignatureXML(const aSignedBytes: TBytes;
  out aSigned: string): Boolean;
var
  vC: TsgcASiCContainer;
  vUTF8: UTF8String;
  vI: Integer;
begin
  Result := False;
  aSigned := '';
  // Try ASiC first
  if Length(aSignedBytes) >= 4 then
  begin
    if (aSignedBytes[0] = $50) and (aSignedBytes[1] = $4B) and
      (aSignedBytes[2] = $03) and (aSignedBytes[3] = $04) then
    begin
      vC := TsgcASiCContainer.Create;
      try
        try
          vC.LoadFromBytes(aSignedBytes);
          aSigned := vC.GetSignatureXML;
          Result := aSigned <> '';
          Exit;
        except
          on E: Exception do
            Log('ASiC parse error: ' + E.Message);
        end;
      finally
        vC.Free;
      end;
    end;
  end;
  // Otherwise treat as UTF-8 XML
  SetLength(vUTF8, Length(aSignedBytes));
  for vI := 0 to Length(aSignedBytes) - 1 do
    vUTF8[vI + 1] := AnsiChar(aSignedBytes[vI]);
  aSigned := UTF8Decode(vUTF8);
  Result := aSigned <> '';
end;

procedure TFormMain.btnLoadSignedClick(Sender: TObject);
var
  vBytes: TBytes;
  vI: Integer;
  vList: TStringList;
begin
  dlgOpen.Filter := 'Signed (*.xml;*.asics;*.asice)|*.xml;*.asics;*.asice|' +
    'All files (*.*)|*.*';
  dlgOpen.FileName := '';
  if not dlgOpen.Execute then
    Exit;
  vBytes := ReadFileAsBytes(dlgOpen.FileName);
  if Length(vBytes) = 0 then
  begin
    Log('Failed to read or empty file: ' + dlgOpen.FileName);
    Exit;
  end;
  // If looks like ZIP (ASiC), summarise
  if (Length(vBytes) >= 4) and (vBytes[0] = $50) and (vBytes[1] = $4B) and
    (vBytes[2] = $03) and (vBytes[3] = $04) then
  begin
    memoVerifyInput.Lines.Text := '[binary ASiC container loaded - ' +
      IntToStr(Length(vBytes)) + ' bytes - ' + dlgOpen.FileName + ']';
    FLastSignedBytes := vBytes;
    if Pos('.asice', LowerCase(dlgOpen.FileName)) > 0 then
      FLastSignedKind := lskASiCE
    else
      FLastSignedKind := lskASiCS;
    Log('Loaded ASiC container.');
  end
  else
  begin
    vList := TStringList.Create;
    try
      try
        vList.LoadFromFile(dlgOpen.FileName);
        memoVerifyInput.Lines.Text := vList.Text;
      except
        on E: Exception do
        begin
          Log('Failed to load XML: ' + E.Message);
          Exit;
        end;
      end;
    finally
      vList.Free;
    end;
    FLastSignedBytes := vBytes;
    FLastSignedKind := lskXML;
    Log('Loaded signed XML.');
  end;
  // unused warning suppressor
  vI := 0;
  vI := vI;
end;

procedure TFormMain.btnUseLastClick(Sender: TObject);
begin
  if FLastSignedKind = lskNone then
  begin
    Log('No signed payload yet. Sign first.');
    Exit;
  end;
  case FLastSignedKind of
    lskXML:
      memoVerifyInput.Lines.Text := FLastSignedXML;
    lskASiCS, lskASiCE:
      memoVerifyInput.Lines.Text := '[binary ASiC container - ' +
        IntToStr(Length(FLastSignedBytes)) + ' bytes - in memory]';
  else
    memoVerifyInput.Lines.Text := '';
  end;
  Log('Using last signed payload.');
end;

procedure TFormMain.btnVerifyClick(Sender: TObject);
var
  vVerifier: TsgcSignatureVerifier;
  vStatus: TsgcVerificationStatus;
  vSigned: string;
  vRawText: string;
  vUTF8: UTF8String;
  vBytes: TBytes;
  vI: Integer;
begin
  vRawText := memoVerifyInput.Lines.Text;
  if (Trim(vRawText) = '') and (FLastSignedKind = lskNone) then
  begin
    Log('Nothing to verify.');
    Exit;
  end;
  // If memo holds the placeholder string, fall back to FLastSignedBytes
  if (Pos('[binary ASiC container', vRawText) = 1) and
    (Length(FLastSignedBytes) > 0) then
  begin
    if not ExtractInnerSignatureXML(FLastSignedBytes, vSigned) then
    begin
      Log('Could not extract signature from container.');
      Exit;
    end;
  end
  else
  begin
    // memo text could be plain XML, or could be a serialised container
    // path: assume it's text. Convert to bytes and let the helper sniff.
    vUTF8 := UTF8Encode(vRawText);
    SetLength(vBytes, Length(vUTF8));
    if Length(vUTF8) > 0 then
      Move(vUTF8[1], vBytes[0], Length(vUTF8));
    if not ExtractInnerSignatureXML(vBytes, vSigned) then
      vSigned := vRawText;
  end;
  if Trim(vSigned) = '' then
  begin
    Log('Empty signature payload after extraction.');
    Exit;
  end;

  Log('Verifying signature...');
  vVerifier := TsgcSignatureVerifier.Create(nil);
  try
    try
      vStatus := vVerifier.Verify(vSigned);
      memoVerifyResult.Lines.Text := 'Status: ' + StatusName(vStatus) +
        sLineBreak + sLineBreak + vVerifier.GetVerificationDetails;
      FLastReport := vVerifier.GetValidationReportXML;
      memoEtsiReport.Lines.Text := FLastReport;
      Log('Verify finished: ' + StatusName(vStatus));
    except
      on E: Exception do
        memoVerifyResult.Lines.Text := 'VERIFY ERROR: ' + E.Message;
    end;
  finally
    vVerifier.Free;
  end;
  // unused suppressor
  vI := 0;
  vI := vI;
end;

procedure TFormMain.btnVerifyLTVClick(Sender: TObject);
var
  vVerifier: TsgcSignatureVerifier;
  vStatus: TsgcVerificationStatus;
  vSigned: string;
  vRawText: string;
  vUTF8: UTF8String;
  vBytes: TBytes;
begin
  vRawText := memoVerifyInput.Lines.Text;
  if (Trim(vRawText) = '') and (FLastSignedKind = lskNone) then
  begin
    Log('Nothing to verify.');
    Exit;
  end;
  if (Pos('[binary ASiC container', vRawText) = 1) and
    (Length(FLastSignedBytes) > 0) then
  begin
    if not ExtractInnerSignatureXML(FLastSignedBytes, vSigned) then
    begin
      Log('Could not extract signature from container.');
      Exit;
    end;
  end
  else
  begin
    vUTF8 := UTF8Encode(vRawText);
    SetLength(vBytes, Length(vUTF8));
    if Length(vUTF8) > 0 then
      Move(vUTF8[1], vBytes[0], Length(vUTF8));
    if not ExtractInnerSignatureXML(vBytes, vSigned) then
      vSigned := vRawText;
  end;
  if Trim(vSigned) = '' then
  begin
    Log('Empty signature payload after extraction.');
    Exit;
  end;

  Log('Verifying signature (LTV)...');
  vVerifier := TsgcSignatureVerifier.Create(nil);
  try
    try
      vStatus := vVerifier.VerifyLTV(vSigned);
      memoVerifyResult.Lines.Text := 'Status (LTV): ' + StatusName(vStatus) +
        sLineBreak + sLineBreak + vVerifier.GetVerificationDetails;
      FLastReport := vVerifier.GetValidationReportXML;
      memoEtsiReport.Lines.Text := FLastReport;
      Log('Verify (LTV) finished: ' + StatusName(vStatus));
    except
      on E: Exception do
        memoVerifyResult.Lines.Text := 'VERIFY ERROR: ' + E.Message;
    end;
  finally
    vVerifier.Free;
  end;
end;

procedure TFormMain.btnSaveReportClick(Sender: TObject);
var
  vList: TStringList;
begin
  if FLastReport = '' then
  begin
    Log('No validation report yet. Verify first.');
    Exit;
  end;
  dlgSave.DefaultExt := 'xml';
  dlgSave.Filter := 'ETSI report (*.xml)|*.xml|All files (*.*)|*.*';
  dlgSave.FileName := 'etsi_119_102-2_report.xml';
  if dlgSave.Execute then
  begin
    vList := TStringList.Create;
    try
      vList.Text := FLastReport;
      try
        vList.SaveToFile(dlgSave.FileName);
        Log('Saved validation report to ' + dlgSave.FileName);
      except
        on E: Exception do
          Log('Save report failed: ' + E.Message);
      end;
    finally
      vList.Free;
    end;
  end;
end;

{ ----- trust list -------------------------------------------------------- }

function TFormMain.StatusName(aStatus: TsgcVerificationStatus): string;
begin
  case aStatus of
    vsValid:
      Result := 'VALID';
    vsInvalid:
      Result := 'INVALID';
    vsIndeterminate:
      Result := 'INDETERMINATE';
    vsCertificateExpired:
      Result := 'CERT_EXPIRED';
    vsCertificateRevoked:
      Result := 'CERT_REVOKED';
    vsTimestampInvalid:
      Result := 'TS_INVALID';
  else
    Result := '?';
  end;
end;

function TFormMain.TrustStatusName(aStatus: TsgcTrustServiceStatus): string;
begin
  case aStatus of
    tssGranted:
      Result := 'GRANTED';
    tssWithdrawn:
      Result := 'WITHDRAWN';
    tssRecognisedAtNationalLevel:
      Result := 'RECOG-NAT';
    tssDeprecatedAtNationalLevel:
      Result := 'DEPREC-NAT';
  else
    Result := 'UNKNOWN';
  end;
end;

function TFormMain.DistinctCountriesCount(const aServices
  : TsgcTrustServiceArray): Integer;
var
  vSeen: TStringList;
  vI: Integer;
begin
  Result := 0;
  if Length(aServices) = 0 then
    Exit;
  vSeen := TStringList.Create;
  try
    vSeen.Sorted := True;
    vSeen.Duplicates := dupIgnore;
    for vI := 0 to High(aServices) do
      if aServices[vI].Country <> '' then
        vSeen.Add(UpperCase(aServices[vI].Country));
    Result := vSeen.Count;
  finally
    vSeen.Free;
  end;
end;

procedure TFormMain.btnRefreshTLClick(Sender: TObject);
var
  vI: Integer;
  vDate: string;
  vItem: TListItem;
  vOK: Boolean;
begin
  if FTrustList = nil then
    FTrustList := TsgcEUTrustList.Create;
  FTrustList.CacheDir := edTrustListCacheDir.Text;
  Log('Refreshing trust list (this may take a while)...');
  Screen.Cursor := crHourGlass;
  try
    vOK := False;
    try
      vOK := FTrustList.Refresh;
    except
      on E: Exception do
        Log('Refresh exception: ' + E.Message);
    end;
    if not vOK then
    begin
      Log('Refresh returned false; trying cache-only load.');
      try
        FTrustList.LoadFromCache;
      except
        on E: Exception do
          Log('Cache load exception: ' + E.Message);
      end;
    end;
  finally
    Screen.Cursor := crDefault;
  end;

  lblTLStatus.Caption := Format('Status: services=%d  countries=%d',
    [Length(FTrustList.Services), DistinctCountriesCount(FTrustList.Services)]);

  lvServices.Items.BeginUpdate;
  try
    lvServices.Items.Clear;
    for vI := 0 to Length(FTrustList.Services) - 1 do
    begin
      vItem := lvServices.Items.Add;
      vItem.Caption := FTrustList.Services[vI].Country;
      vItem.SubItems.Add(FTrustList.Services[vI].TSPName);
      vItem.SubItems.Add(FTrustList.Services[vI].ServiceName);
      vItem.SubItems.Add(TrustStatusName(FTrustList.Services[vI].Status));
      if FTrustList.Services[vI].StatusStartingTime > 0 then
        vDate := DateTimeToStr(FTrustList.Services[vI].StatusStartingTime)
      else
        vDate := '';
      vItem.SubItems.Add(vDate);
    end;
  finally
    lvServices.Items.EndUpdate;
  end;
  if FTrustList.LastError <> '' then
    Log('LastError: ' + FTrustList.LastError);
end;

procedure TFormMain.btnLookupClick(Sender: TObject);
var
  vDER: TBytes;
  vSvc: TsgcTrustService;
  vFound: Boolean;
begin
  if FTrustList = nil then
  begin
    Log('Refresh the trust list first.');
    Exit;
  end;
  if Trim(edLookupCertFile.Text) = '' then
  begin
    Log('Pick a certificate file first.');
    Exit;
  end;
  vDER := CertFileToDER(edLookupCertFile.Text);
  if Length(vDER) = 0 then
  begin
    lblLookupResult.Caption := 'Result: failed to read/parse certificate';
    Exit;
  end;
  vFound := FTrustList.FindServiceForCertificate(vDER, Now, vSvc);
  if vFound then
    lblLookupResult.Caption := 'Result: QUALIFIED (' + vSvc.Country + ' / ' +
      vSvc.TSPName + ' / ' + vSvc.ServiceName + ')'
  else
    lblLookupResult.Caption :=
      'Result: NOT FOUND in EUTL (self-signed or not from a listed QTSP)';
end;

end.
```

