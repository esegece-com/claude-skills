# TsgcAWSKMSKeyProvider - Example

Full source of `frmMain.pas` from the **KeyProvider_AWS** demo, which uses `TsgcAWSKMSKeyProvider`.

API reference: [TsgcAWSKMSKeyProvider](../reference/api/TsgcAWSKMSKeyProvider.md)
Source demo: `KeyProvider_AWS` (file `frmMain.pas`)

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
  sgcSign_CAdES, sgcSign_KeyProvider_AWS;

type
  TFormMain = class(TForm)
    pnlTop: TPanel;
    lblAccessKey: TLabel;
    edAccessKey: TEdit;
    lblSecretKey: TLabel;
    edSecretKey: TEdit;
    lblRegion: TLabel;
    edRegion: TEdit;
    lblKeyId: TLabel;
    edKeyId: TEdit;
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
    FProvider: TsgcAWSKMSKeyProvider;
    procedure Log(const aMsg: string);
  end;

var
  FormMain: TFormMain;

implementation

{$R *.dfm}

procedure TFormMain.FormCreate(Sender: TObject);
begin
  FProvider := nil;
  edRegion.Text := 'us-east-1';
  Log('AWS KMS Key Provider demo ready. Enter credentials and connect.');
end;

procedure TFormMain.btnConnectClick(Sender: TObject);
begin
  if Trim(edAccessKey.Text) = '' then
  begin
    Log('ERROR: Please enter Access Key ID');
    Exit;
  end;

  if Trim(edSecretKey.Text) = '' then
  begin
    Log('ERROR: Please enter Secret Access Key');
    Exit;
  end;

  if Trim(edKeyId.Text) = '' then
  begin
    Log('ERROR: Please enter KMS Key ID or ARN');
    Exit;
  end;

  Log('Connecting to AWS KMS...');

  if FProvider <> nil then
    FreeAndNil(FProvider);

  FProvider := TsgcAWSKMSKeyProvider.Create(nil);
  try
    FProvider.AccessKeyId := edAccessKey.Text;
    FProvider.SecretAccessKey := edSecretKey.Text;
    FProvider.Region := edRegion.Text;
    FProvider.KeyId := edKeyId.Text;
    FProvider.Connect;
    Log('SUCCESS: Connected to AWS KMS');
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
    Log('ERROR: Please connect to AWS KMS first');
    Exit;
  end;

  if Trim(memoData.Lines.Text) = '' then
  begin
    Log('ERROR: Please enter data to sign');
    Exit;
  end;

  Log('Signing with AWS KMS...');

  vSigner := TsgcCAdESSigner.Create(nil);
  try
    try
      vSigner.KeyProvider := FProvider as IsgcKeyProvider;
      vSigner.Level := clBES;
      vSigner.Detached := True;

      vData := TEncoding.UTF8.GetBytes(memoData.Lines.Text);
      vBase64 := vSigner.SignDataBase64(vData);
      memoSignature.Lines.Text := vBase64;

      Log('SUCCESS: Data signed with CAdES-BES using AWS KMS');
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

