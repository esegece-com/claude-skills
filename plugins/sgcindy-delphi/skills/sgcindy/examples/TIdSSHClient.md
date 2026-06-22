# TIdSSHClient - Example

Full source of `fSSHClient.pas` from the **SSHClient** demo, which uses `TIdSSHClient`.

API reference: [TIdSSHClient](../reference/api/TIdSSHClient.md)
Source demo: `SSHClient` (file `fSSHClient.pas`)

```pascal
{ ***************************************************************************
  sgcIndy SSH Client Demo

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit fSSHClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls,
  // sgc
  IdSSHClient, IdSSHTypes, IdSSHClasses, IdGlobal;

type
  TfrmSSHClient = class(TForm)
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
    lblCommand: TLabel;
    txtCommand: TEdit;
    btnExecute: TButton;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnConnectClick(Sender: TObject);
    procedure btnDisconnectClick(Sender: TObject);
    procedure btnExecuteClick(Sender: TObject);
  private
    fSSHClient: TIdSSHClient;
    procedure DoLog(const aText: string);
    procedure OnSSHConnect(Sender: TObject);
    procedure OnSSHDisconnect(Sender: TObject; const aReason: string;
      aCode: Integer);
    procedure OnSSHAuthSuccess(Sender: TObject);
    procedure OnSSHChannelData(Sender: TObject; aChannelId: Cardinal;
      const aData: TIdBytes);
    procedure OnSSHError(Sender: TObject; const aError: string;
      aErrorCode: Integer);
    procedure OnSSHHostKey(Sender: TObject; const aHostKeyType: string;
      const aFingerprint: string; var aAction: TIdSSHHostKeyVerification);
  public
    { Public declarations }
  end;

var
  frmSSHClient: TfrmSSHClient;

implementation

{$R *.dfm}

procedure TfrmSSHClient.FormCreate(Sender: TObject);
begin
  fSSHClient := TIdSSHClient.Create(nil);
  fSSHClient.OnSSHConnect := OnSSHConnect;
  fSSHClient.OnSSHDisconnect := OnSSHDisconnect;
  fSSHClient.OnSSHAuthSuccess := OnSSHAuthSuccess;
  fSSHClient.OnSSHChannelData := OnSSHChannelData;
  fSSHClient.OnSSHError := OnSSHError;
  fSSHClient.OnSSHHostKey := OnSSHHostKey;
end;

procedure TfrmSSHClient.FormDestroy(Sender: TObject);
begin
  if fSSHClient.Active then
    fSSHClient.Disconnect;
  FreeAndNil(fSSHClient);
end;

procedure TfrmSSHClient.DoLog(const aText: string);
begin
  TThread.Queue(nil, procedure
    begin
      if Assigned(memoLog) then
        memoLog.Lines.Add(aText);
    end);
end;

procedure TfrmSSHClient.OnSSHConnect(Sender: TObject);
begin
  DoLog('Connected to ' + fSSHClient.Host + ':' + IntToStr(fSSHClient.Port));
end;

procedure TfrmSSHClient.OnSSHDisconnect(Sender: TObject; const aReason: string;
aCode: Integer);
begin
  DoLog('Disconnected: ' + aReason + ' (code ' + IntToStr(aCode) + ')');
end;

procedure TfrmSSHClient.OnSSHAuthSuccess(Sender: TObject);
begin
  DoLog('Authenticated successfully');
end;

procedure TfrmSSHClient.OnSSHChannelData(Sender: TObject; aChannelId: Cardinal;
const aData: TIdBytes);
var
  vText: string;
begin
  vText := TEncoding.UTF8.GetString(aData);
  DoLog(vText);
end;

procedure TfrmSSHClient.OnSSHError(Sender: TObject; const aError: string;
aErrorCode: Integer);
begin
  DoLog('Error [' + IntToStr(aErrorCode) + ']: ' + aError);
end;

procedure TfrmSSHClient.OnSSHHostKey(Sender: TObject;
const aHostKeyType: string; const aFingerprint: string;
var aAction: TIdSSHHostKeyVerification);
begin
  DoLog('Host key (' + aHostKeyType + '): ' + aFingerprint);
  aAction := sshHostKeyAccept;
end;

procedure TfrmSSHClient.btnConnectClick(Sender: TObject);
begin
  memoLog.Lines.Clear;
  fSSHClient.Host := txtHost.Text;
  fSSHClient.Port := StrToIntDef(txtPort.Text, 22);
  fSSHClient.Authentication.Username := txtUsername.Text;
  fSSHClient.Authentication.Password := txtPassword.Text;
  DoLog('Connecting to ' + fSSHClient.Host + ':' +
    IntToStr(fSSHClient.Port) + '...');
  fSSHClient.Connect;
end;

procedure TfrmSSHClient.btnDisconnectClick(Sender: TObject);
begin
  fSSHClient.Disconnect;
end;

procedure TfrmSSHClient.btnExecuteClick(Sender: TObject);
var
  vResult: string;
begin
  if not fSSHClient.Active then
  begin
    DoLog('Not connected');
    Exit;
  end;
  if Trim(txtCommand.Text) = '' then
  begin
    DoLog('Please enter a command');
    Exit;
  end;
  DoLog('> ' + txtCommand.Text);
  try
    vResult := fSSHClient.Execute(txtCommand.Text);
    DoLog(vResult);
  except
    on E: Exception do
      DoLog('Execute error: ' + E.Message);
  end;
end;

end.
```

