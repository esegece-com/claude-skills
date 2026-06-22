# TsgcPAdESSigner - Example

Full source of `frmMain.pas` from the **PAdES** demo, which uses `TsgcPAdESSigner`.

API reference: [TsgcPAdESSigner](../reference/api/TsgcPAdESSigner.md)
Source demo: `PAdES` (file `frmMain.pas`)

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
  sgcSign_PAdES, sgcSign_KeyProvider_WinCertStore,
  sgcSign_KeyProvider_PEM, sgcSign_KeyProvider_PFX;

type
  TFormMain = class(TForm)
    memoLog: TMemo;
    btnSign: TButton;
    btnBrowse: TButton;
    btnListCerts: TButton;
    edCertFilter: TEdit;
    edInputFile: TEdit;
    lblCertFilter: TLabel;
    lblInputFile: TLabel;
    lblLog: TLabel;
    pnlTop: TPanel;
    pnlClient: TPanel;
    dlgOpen: TOpenDialog;
    rgCertSource: TRadioGroup;
    lblCertFile: TLabel;
    edCertFile: TEdit;
    btnBrowseCert: TButton;
    lblKeyFile: TLabel;
    edKeyFile: TEdit;
    btnBrowseKey: TButton;
    lblKeyPassword: TLabel;
    edKeyPassword: TEdit;
    dlgOpenKey: TOpenDialog;
    procedure btnSignClick(Sender: TObject);
    procedure btnBrowseClick(Sender: TObject);
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
  UpdateCertSourceUI;
  Log('PAdES demo ready. Choose certificate source, select a PDF file, and click Sign.');
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
  dlgOpenKey.Filter := 'Certificate / Bundle (*.pem;*.crt;*.cer;*.pfx;*.p12)|' +
    '*.pem;*.crt;*.cer;*.pfx;*.p12|All files (*.*)|*.*';
  dlgOpenKey.FileName := edCertFile.Text;
  if dlgOpenKey.Execute then
    edCertFile.Text := dlgOpenKey.FileName;
end;

procedure TFormMain.btnBrowseKeyClick(Sender: TObject);
begin
  dlgOpenKey.Filter := 'PEM key (*.pem;*.key)|*.pem;*.key|All files (*.*)|*.*';
  dlgOpenKey.FileName := edKeyFile.Text;
  if dlgOpenKey.Execute then
    edKeyFile.Text := dlgOpenKey.FileName;
end;

procedure TFormMain.btnBrowseClick(Sender: TObject);
begin
  if dlgOpen.Execute then
    edInputFile.Text := dlgOpen.FileName;
end;

procedure TFormMain.btnSignClick(Sender: TObject);
var
  vSigner: TsgcPAdESSigner;
  vKeyProvider: TComponent;
  vOutputFile: string;
  vCertFile: string;
  vKeyFile: string;
  vUsePFX: Boolean;
  oWin: TsgcWindowsCertStoreProvider;
  oPFX: TsgcPFXKeyProvider;
  oPEM: TsgcPEMKeyProvider;
begin
  if Trim(edInputFile.Text) = '' then
  begin
    Log('ERROR: Please select an input PDF file');
    Exit;
  end;

  if not FileExists(edInputFile.Text) then
  begin
    Log('ERROR: File not found: ' + edInputFile.Text);
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

  Log('Signing PDF with PAdES profile...');

  vSigner := TsgcPAdESSigner.Create(nil);
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
      vSigner.Reason := 'Demo signature';
      vSigner.Location := 'Spain';
      vSigner.SignerName := 'sgcSign Demo';

      vOutputFile := ChangeFileExt(edInputFile.Text, '_signed.pdf');
      vSigner.SignPDFFile(edInputFile.Text, vOutputFile);

      Log('SUCCESS: PDF signed with PAdES profile');
      Log('Output file: ' + vOutputFile);
    except
      on E: Exception do
        Log('ERROR: ' + E.Message);
    end;
  finally
    vSigner.Free;
    vKeyProvider.Free;
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

