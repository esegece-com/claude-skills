# TsgcPKCS11Provider - Example

Full source of `frmMain.pas` from the **KeyProvider_PKCS11** demo, which uses `TsgcPKCS11Provider`.

API reference: [TsgcPKCS11Provider](../reference/api/TsgcPKCS11Provider.md)
Source demo: `KeyProvider_PKCS11` (file `frmMain.pas`)

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
  sgcSign_CAdES, sgcSign_KeyProvider_PKCS11;

type
  TFormMain = class(TForm)
    pnlTop: TPanel;
    lblLibrary: TLabel;
    edLibrary: TEdit;
    btnBrowse: TButton;
    lblSlot: TLabel;
    edSlot: TEdit;
    lblPIN: TLabel;
    edPIN: TEdit;
    lblCertLabel: TLabel;
    edCertLabel: TEdit;
    btnConnect: TButton;
    btnListSlots: TButton;
    btnListCerts: TButton;
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
    procedure btnBrowseClick(Sender: TObject);
    procedure btnConnectClick(Sender: TObject);
    procedure btnListSlotsClick(Sender: TObject);
    procedure btnListCertsClick(Sender: TObject);
    procedure btnSignClick(Sender: TObject);
  private
    FProvider: TsgcPKCS11Provider;
    procedure Log(const aMsg: string);
  end;

var
  FormMain: TFormMain;

implementation

{$R *.dfm}

procedure TFormMain.FormCreate(Sender: TObject);
begin
  FProvider := nil;
  edSlot.Text := '0';
  Log('PKCS#11 Key Provider demo ready. Select PKCS#11 library DLL.');
end;

procedure TFormMain.btnBrowseClick(Sender: TObject);
begin
  if dlgOpen.Execute then
    edLibrary.Text := dlgOpen.FileName;
end;

procedure TFormMain.btnConnectClick(Sender: TObject);
begin
  if Trim(edLibrary.Text) = '' then
  begin
    Log('ERROR: Please select a PKCS#11 library');
    Exit;
  end;

  if Trim(edPIN.Text) = '' then
  begin
    Log('ERROR: Please enter PIN');
    Exit;
  end;

  Log('Connecting to PKCS#11 token...');

  if FProvider <> nil then
  begin
    FProvider.Disconnect;
    FProvider.Free;
  end;

  FProvider := TsgcPKCS11Provider.Create(nil);
  try
    FProvider.LibraryPath := edLibrary.Text;
    FProvider.SlotIndex := StrToIntDef(edSlot.Text, 0);
    FProvider.PIN := edPIN.Text;
    if Trim(edCertLabel.Text) <> '' then
      FProvider.CertificateLabel := edCertLabel.Text;
    FProvider.Connect;
    Log('SUCCESS: Connected. Certificate: ' + FProvider.Certificate.Subject);
  except
    on E: Exception do
    begin
      Log('ERROR: ' + E.Message);
      FreeAndNil(FProvider);
    end;
  end;
end;

procedure TFormMain.btnListSlotsClick(Sender: TObject);
var
  vProvider: TsgcPKCS11Provider;
  vSlots: TStringList;
  I: Integer;
begin
  if Trim(edLibrary.Text) = '' then
  begin
    Log('ERROR: Please select a PKCS#11 library');
    Exit;
  end;

  Log('Listing available slots...');

  vProvider := TsgcPKCS11Provider.Create(nil);
  try
    try
      vProvider.LibraryPath := edLibrary.Text;
      vSlots := vProvider.EnumerateSlots;
      try
        if vSlots.Count = 0 then
          Log('No slots found.')
        else
        begin
          Log('Found ' + IntToStr(vSlots.Count) + ' slots:');
          for I := 0 to vSlots.Count - 1 do
            Log('  [' + IntToStr(I) + '] ' + vSlots[I]);
        end;
      finally
        vSlots.Free;
      end;
    except
      on E: Exception do
        Log('ERROR: ' + E.Message);
    end;
  finally
    vProvider.Free;
  end;
end;

procedure TFormMain.btnListCertsClick(Sender: TObject);
var
  vProvider: TsgcPKCS11Provider;
  vCerts: TStringList;
  I: Integer;
begin
  if Trim(edLibrary.Text) = '' then
  begin
    Log('ERROR: Please select a PKCS#11 library');
    Exit;
  end;

  if Trim(edPIN.Text) = '' then
  begin
    Log('ERROR: Please enter PIN');
    Exit;
  end;

  Log('Listing certificates on token...');

  vProvider := TsgcPKCS11Provider.Create(nil);
  try
    try
      vProvider.LibraryPath := edLibrary.Text;
      vProvider.SlotIndex := StrToIntDef(edSlot.Text, 0);
      vProvider.PIN := edPIN.Text;
      vCerts := vProvider.EnumerateCertificates;
      try
        if vCerts.Count = 0 then
          Log('No certificates found.')
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
  finally
    vProvider.Free;
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
    Log('ERROR: Please connect to token first');
    Exit;
  end;

  if Trim(memoData.Lines.Text) = '' then
  begin
    Log('ERROR: Please enter data to sign');
    Exit;
  end;

  Log('Signing with PKCS#11 token...');

  vSigner := TsgcCAdESSigner.Create(nil);
  try
    try
      vSigner.KeyProvider := FProvider as IsgcKeyProvider;
      vSigner.Level := clBES;
      vSigner.Detached := True;

      vData := TEncoding.UTF8.GetBytes(memoData.Lines.Text);
      vBase64 := vSigner.SignDataBase64(vData);
      memoSignature.Lines.Text := vBase64;

      Log('SUCCESS: Data signed with CAdES-BES using PKCS#11');
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

