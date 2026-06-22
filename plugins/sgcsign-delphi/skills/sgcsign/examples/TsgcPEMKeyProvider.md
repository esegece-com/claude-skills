# TsgcPEMKeyProvider - Example

Full source of `frmMain.pas` from the **CAdES** demo, which uses `TsgcPEMKeyProvider`.

API reference: [TsgcPEMKeyProvider](../reference/api/TsgcPEMKeyProvider.md)
Source demo: `CAdES` (file `frmMain.pas`)

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
  sgcSign_CAdES, sgcSign_KeyProvider_WinCertStore,
  sgcSign_KeyProvider_PEM, sgcSign_KeyProvider_PFX,
  sgcSign_Base64;

type
  TFormMain = class(TForm)
    memoData: TMemo;
    memoSignature: TMemo;
    memoLog: TMemo;
    btnSign: TButton;
    btnSaveP7S: TButton;
    btnListCerts: TButton;
    edCertFilter: TEdit;
    lblCertFilter: TLabel;
    lblData: TLabel;
    lblSignature: TLabel;
    lblLog: TLabel;
    pnlTop: TPanel;
    pnlClient: TPanel;
    dlgSave: TSaveDialog;
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
    procedure btnSaveP7SClick(Sender: TObject);
    procedure btnListCertsClick(Sender: TObject);
    procedure FormCreate(Sender: TObject);
    procedure rgCertSourceClick(Sender: TObject);
    procedure btnBrowseCertClick(Sender: TObject);
    procedure btnBrowseKeyClick(Sender: TObject);
    procedure edCertFileChange(Sender: TObject);
  private
    FLastSignature: TBytes;
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
  UpdateCertSourceUI;
  Log('CAdES demo ready. Choose certificate source and click Sign.');
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
  vSigner: TsgcCAdESSigner;
  vKeyProvider: TComponent;
  vCertFile: string;
  vKeyFile: string;
  vUsePFX: Boolean;
  vData: TBytes;
  vBase64: string;
  oWin: TsgcWindowsCertStoreProvider;
  oPFX: TsgcPFXKeyProvider;
  oPEM: TsgcPEMKeyProvider;
begin
  if Trim(memoData.Lines.Text) = '' then
  begin
    Log('ERROR: Please enter data to sign');
    Exit;
  end;

  if rgCertSource.ItemIndex = 0 then
  begin
    if Trim(edCertFilter.Text) = '' then
    begin
      Log('ERROR: Please enter a certificate filter (CN or NIF)');
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

  Log('Signing data with CAdES-BES...');

  vSigner := TsgcCAdESSigner.Create(nil);
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
      vSigner.Level := clBES;
      vSigner.Detached := True;

      vData := TEncoding.UTF8.GetBytes(memoData.Lines.Text);
      FLastSignature := vSigner.SignData(vData);

      vBase64 := vSigner.SignDataBase64(vData);
      memoSignature.Lines.Text := vBase64;

      Log('SUCCESS: Data signed with CAdES-BES');
      Log('Signature size: ' + IntToStr(Length(FLastSignature)) + ' bytes');
    except
      on E: Exception do
        Log('ERROR: ' + E.Message);
    end;
  finally
    vSigner.Free;
    vKeyProvider.Free;
  end;
end;

procedure TFormMain.btnSaveP7SClick(Sender: TObject);
var
  vStream: TFileStream;
begin
  if Length(FLastSignature) = 0 then
  begin
    Log('ERROR: No signature to save. Sign data first.');
    Exit;
  end;

  dlgSave.FileName := 'signature.p7s';
  if dlgSave.Execute then
  begin
    vStream := TFileStream.Create(dlgSave.FileName, fmCreate);
    try
      vStream.WriteBuffer(FLastSignature[0], Length(FLastSignature));
      Log('Saved signature to: ' + dlgSave.FileName);
    finally
      vStream.Free;
    end;
  end;
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

