# TsgcGCloudKMSKeyProvider - Example

Full source of `frmMain.pas` from the **KeyProvider_GCloud** demo, which uses `TsgcGCloudKMSKeyProvider`.

API reference: [TsgcGCloudKMSKeyProvider](../reference/api/TsgcGCloudKMSKeyProvider.md)
Source demo: `KeyProvider_GCloud` (file `frmMain.pas`)

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
  sgcSign_CAdES, sgcSign_KeyProvider_GCloud;

type
  TFormMain = class(TForm)
    pnlTop: TPanel;
    lblProjectId: TLabel;
    edProjectId: TEdit;
    lblLocationId: TLabel;
    edLocationId: TEdit;
    lblKeyRingId: TLabel;
    edKeyRingId: TEdit;
    lblKeyId: TLabel;
    edKeyId: TEdit;
    lblKeyVersion: TLabel;
    edKeyVersion: TEdit;
    lblServiceAccount: TLabel;
    memoServiceAccount: TMemo;
    btnConnect: TButton;
    btnLoadJSON: TButton;
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
    procedure btnLoadJSONClick(Sender: TObject);
    procedure btnConnectClick(Sender: TObject);
    procedure btnSignClick(Sender: TObject);
  private
    FProvider: TsgcGCloudKMSKeyProvider;
    procedure Log(const aMsg: string);
  end;

var
  FormMain: TFormMain;

implementation

{$R *.dfm}

procedure TFormMain.FormCreate(Sender: TObject);
begin
  FProvider := nil;
  edLocationId.Text := 'us';
  edKeyVersion.Text := '1';
  Log('Google Cloud KMS demo ready. Enter project details and connect.');
end;

procedure TFormMain.btnLoadJSONClick(Sender: TObject);
var
  vList: TStringList;
begin
  dlgOpen.Filter := 'JSON Files (*.json)|*.json|All Files (*.*)|*.*';
  if dlgOpen.Execute then
  begin
    vList := TStringList.Create;
    try
      vList.LoadFromFile(dlgOpen.FileName);
      memoServiceAccount.Lines.Text := vList.Text;
      Log('Service account JSON loaded from: ' + dlgOpen.FileName);
    finally
      vList.Free;
    end;
  end;
end;

procedure TFormMain.btnConnectClick(Sender: TObject);
begin
  if Trim(edProjectId.Text) = '' then
  begin
    Log('ERROR: Please enter Project ID');
    Exit;
  end;

  if Trim(edKeyRingId.Text) = '' then
  begin
    Log('ERROR: Please enter Key Ring ID');
    Exit;
  end;

  if Trim(edKeyId.Text) = '' then
  begin
    Log('ERROR: Please enter Key ID');
    Exit;
  end;

  if Trim(memoServiceAccount.Lines.Text) = '' then
  begin
    Log('ERROR: Please provide service account JSON');
    Exit;
  end;

  Log('Connecting to Google Cloud KMS...');

  if FProvider <> nil then
    FreeAndNil(FProvider);

  FProvider := TsgcGCloudKMSKeyProvider.Create(nil);
  try
    FProvider.ProjectId := edProjectId.Text;
    FProvider.LocationId := edLocationId.Text;
    FProvider.KeyRingId := edKeyRingId.Text;
    FProvider.KeyId := edKeyId.Text;
    FProvider.KeyVersion := edKeyVersion.Text;
    FProvider.ServiceAccountJSON := memoServiceAccount.Lines.Text;
    FProvider.Connect;
    Log('SUCCESS: Connected to Google Cloud KMS');
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
    Log('ERROR: Please connect to Google Cloud KMS first');
    Exit;
  end;

  if Trim(memoData.Lines.Text) = '' then
  begin
    Log('ERROR: Please enter data to sign');
    Exit;
  end;

  Log('Signing with Google Cloud KMS...');

  vSigner := TsgcCAdESSigner.Create(nil);
  try
    try
      vSigner.KeyProvider := FProvider as IsgcKeyProvider;
      vSigner.Level := clBES;
      vSigner.Detached := True;

      vData := TEncoding.UTF8.GetBytes(memoData.Lines.Text);
      vBase64 := vSigner.SignDataBase64(vData);
      memoSignature.Lines.Text := vBase64;

      Log('SUCCESS: Data signed with CAdES-BES using Google Cloud KMS');
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

