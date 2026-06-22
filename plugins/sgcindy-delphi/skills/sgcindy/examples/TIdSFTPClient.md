# TIdSFTPClient - Example

Full source of `fSFTPClient.pas` from the **SFTPClient** demo, which uses `TIdSFTPClient`.

API reference: [TIdSFTPClient](../reference/api/TIdSFTPClient.md)
Source demo: `SFTPClient` (file `fSFTPClient.pas`)

```pascal
{ ***************************************************************************
  sgcIndy SFTP Client Demo

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit fSFTPClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls,
  // sgc
  IdSFTPClient, IdSSHTypes, IdSSHClasses;

type
  TfrmSFTPClient = class(TForm)
    lblHost: TLabel;
    txtHost: TEdit;
    lblPort: TLabel;
    txtPort: TEdit;
    lblUsername: TLabel;
    txtUsername: TEdit;
    lblPassword: TLabel;
    txtPassword: TEdit;
    btnConnect: TButton;
    btnDisconnect: TButton;
    lblRemotePath: TLabel;
    txtRemotePath: TEdit;
    lblLocalPath: TLabel;
    txtLocalPath: TEdit;
    btnListDir: TButton;
    btnUpload: TButton;
    btnDownload: TButton;
    memoListing: TMemo;
    memoLog: TMemo;
    lblListing: TLabel;
    lblLog: TLabel;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnConnectClick(Sender: TObject);
    procedure btnDisconnectClick(Sender: TObject);
    procedure btnListDirClick(Sender: TObject);
    procedure btnUploadClick(Sender: TObject);
    procedure btnDownloadClick(Sender: TObject);
  private
    fSFTPClient: TIdSFTPClient;
    procedure DoLog(const aText: string);
    procedure OnSFTPConnect(Sender: TObject);
    procedure OnSFTPDisconnect(Sender: TObject);
    procedure OnSFTPError(Sender: TObject; aErrorCode: Integer;
      const aErrorMessage: string);
    procedure OnSFTPProgress(Sender: TObject; const aFileName: string;
      aTransferred, aTotal: Int64; var aCancel: Boolean);
    procedure OnSSHHostKey(Sender: TObject; const aHostKeyType: string;
      const aFingerprint: string; var aAction: TIdSSHHostKeyVerification);
  public
    { Public declarations }
  end;

var
  frmSFTPClient: TfrmSFTPClient;

implementation

{$R *.dfm}

procedure TfrmSFTPClient.FormCreate(Sender: TObject);
begin
  fSFTPClient := TIdSFTPClient.Create(nil);
  fSFTPClient.OnSFTPConnect := OnSFTPConnect;
  fSFTPClient.OnSFTPDisconnect := OnSFTPDisconnect;
  fSFTPClient.OnSFTPError := OnSFTPError;
  fSFTPClient.OnSFTPProgress := OnSFTPProgress;
  fSFTPClient.OnSSHHostKey := OnSSHHostKey;
end;

procedure TfrmSFTPClient.FormDestroy(Sender: TObject);
begin
  if fSFTPClient.Active then
    fSFTPClient.Disconnect;
  FreeAndNil(fSFTPClient);
end;

procedure TfrmSFTPClient.DoLog(const aText: string);
begin
  TThread.Queue(nil, procedure
    begin
      if Assigned(memoLog) then
        memoLog.Lines.Add(aText);
    end);
end;

procedure TfrmSFTPClient.OnSFTPConnect(Sender: TObject);
begin
  DoLog('SFTP connected to ' + fSFTPClient.Host + ':' +
    IntToStr(fSFTPClient.Port));
end;

procedure TfrmSFTPClient.OnSFTPDisconnect(Sender: TObject);
begin
  DoLog('SFTP disconnected');
end;

procedure TfrmSFTPClient.OnSFTPError(Sender: TObject; aErrorCode: Integer;
const aErrorMessage: string);
begin
  DoLog('SFTP Error [' + IntToStr(aErrorCode) + ']: ' + aErrorMessage);
end;

procedure TfrmSFTPClient.OnSFTPProgress(Sender: TObject;
const aFileName: string; aTransferred, aTotal: Int64; var aCancel: Boolean);
begin
  if aTotal > 0 then
    DoLog('Transfer: ' + aFileName + ' - ' + IntToStr(aTransferred) + ' / ' +
      IntToStr(aTotal) + ' bytes (' + IntToStr((aTransferred * 100)
      div aTotal) + '%)')
  else
    DoLog('Transfer: ' + aFileName + ' - ' + IntToStr(aTransferred) + ' bytes');
end;

procedure TfrmSFTPClient.OnSSHHostKey(Sender: TObject;
const aHostKeyType: string; const aFingerprint: string;
var aAction: TIdSSHHostKeyVerification);
begin
  DoLog('Host key (' + aHostKeyType + '): ' + aFingerprint);
  aAction := sshHostKeyAccept;
end;

procedure TfrmSFTPClient.btnConnectClick(Sender: TObject);
begin
  memoLog.Lines.Clear;
  fSFTPClient.Host := txtHost.Text;
  fSFTPClient.Port := StrToIntDef(txtPort.Text, 22);
  fSFTPClient.Authentication.Username := txtUsername.Text;
  fSFTPClient.Authentication.Password := txtPassword.Text;
  fSFTPClient.Algorithms.Ciphers := 'aes256-ctr,aes192-ctr,aes128-ctr';
  fSFTPClient.SSHOptions.OpenSSL_Options.APIVersion := sslAPIOpenSSL3;
  DoLog('Connecting to ' + fSFTPClient.Host + ':' +
    IntToStr(fSFTPClient.Port) + '...');
  try
    fSFTPClient.Connect;
  except
    on E: Exception do
      DoLog('Connect error: ' + E.Message);
  end;
end;

procedure TfrmSFTPClient.btnDisconnectClick(Sender: TObject);
begin
  fSFTPClient.Disconnect;
end;

procedure TfrmSFTPClient.btnListDirClick(Sender: TObject);
var
  vItems: TIdSFTPDirectoryItems;
  I: Integer;
  vLine: string;
  vItem: TIdSFTPDirectoryItem;
begin
  if not fSFTPClient.Active then
  begin
    DoLog('Not connected');
    Exit;
  end;
  memoListing.Lines.Clear;
  DoLog('Listing directory: ' + txtRemotePath.Text);
  try
    vItems := fSFTPClient.ListDirectory(txtRemotePath.Text);
    try
      for I := 0 to vItems.Count - 1 do
      begin
        vItem := vItems[I];
        if vItem.LongName <> '' then
          vLine := vItem.LongName
        else
          vLine := vItem.FileName;
        memoListing.Lines.Add(vLine);
      end;
      DoLog('Listed ' + IntToStr(vItems.Count) + ' items');
    finally
      vItems.Free;
    end;
  except
    on E: Exception do
      DoLog('List directory error: ' + E.Message);
  end;
end;

procedure TfrmSFTPClient.btnUploadClick(Sender: TObject);
begin
  if not fSFTPClient.Active then
  begin
    DoLog('Not connected');
    Exit;
  end;
  if Trim(txtLocalPath.Text) = '' then
  begin
    DoLog('Please enter a local file path');
    Exit;
  end;
  if Trim(txtRemotePath.Text) = '' then
  begin
    DoLog('Please enter a remote file path');
    Exit;
  end;
  DoLog('Uploading ' + txtLocalPath.Text + ' -> ' + txtRemotePath.Text);
  try
    fSFTPClient.Put(txtLocalPath.Text, txtRemotePath.Text);
    DoLog('Upload complete');
  except
    on E: Exception do
      DoLog('Upload error: ' + E.Message);
  end;
end;

procedure TfrmSFTPClient.btnDownloadClick(Sender: TObject);
begin
  if not fSFTPClient.Active then
  begin
    DoLog('Not connected');
    Exit;
  end;
  if Trim(txtRemotePath.Text) = '' then
  begin
    DoLog('Please enter a remote file path');
    Exit;
  end;
  if Trim(txtLocalPath.Text) = '' then
  begin
    DoLog('Please enter a local file path');
    Exit;
  end;
  DoLog('Downloading ' + txtRemotePath.Text + ' -> ' + txtLocalPath.Text);
  try
    fSFTPClient.Get(txtRemotePath.Text, txtLocalPath.Text);
    DoLog('Download complete');
  except
    on E: Exception do
      DoLog('Download error: ' + E.Message);
  end;
end;

end.
```

