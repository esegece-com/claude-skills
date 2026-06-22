# TIdPOP3 - Example

Full source of `fPOP3Client.pas` from the **POP3Client** demo, which uses `TIdPOP3`.

API reference: [TIdPOP3](../reference/api/TIdPOP3.md)
Source demo: `POP3Client` (file `fPOP3Client.pas`)

```pascal
{ ***************************************************************************
  sgcIndy POP3 Client Demo

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit fPOP3Client;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls, IdIOHandler, IdIOHandlerSocket,
  IdIOHandlerStack, IdSSL, IdSSLOpenSSL, IdSSLOpenSSLHeaders,
  IdBaseComponent, IdComponent, IdTCPConnection, IdTCPClient,
  IdExplicitTLSClientServerBase, IdMessageClient, IdPOP3, IdMessage;

type
  TfrmPOP3Client = class(TForm)
    lblHost: TLabel;
    txtHost: TEdit;
    lblPort: TLabel;
    txtPort: TEdit;
    lblUsername: TLabel;
    txtUsername: TEdit;
    lblPassword: TLabel;
    txtPassword: TEdit;
    lblSSL: TLabel;
    cboOpenSSLAPI: TComboBox;
    cboTLSVersion: TComboBox;
    btnConnect: TButton;
    btnDisconnect: TButton;
    btnCheckMessages: TButton;
    lblMsgNum: TLabel;
    txtMsgNum: TEdit;
    btnRetrieveMessage: TButton;
    btnDeleteMessage: TButton;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnConnectClick(Sender: TObject);
    procedure btnDisconnectClick(Sender: TObject);
    procedure btnCheckMessagesClick(Sender: TObject);
    procedure btnRetrieveMessageClick(Sender: TObject);
    procedure btnDeleteMessageClick(Sender: TObject);
  private
    FIdPOP3: TIdPOP3;
    FIdSSL: TIdSSLIOHandlerSocketOpenSSL;
    procedure DoLog(const aText: string);
  public
    { Public declarations }
  end;

var
  frmPOP3Client: TfrmPOP3Client;

implementation

{$R *.dfm}

procedure TfrmPOP3Client.FormCreate(Sender: TObject);
begin
  FIdPOP3 := TIdPOP3.Create(nil);
  FIdSSL := TIdSSLIOHandlerSocketOpenSSL.Create(nil);
end;

procedure TfrmPOP3Client.FormDestroy(Sender: TObject);
begin
  if FIdPOP3.Connected then
    FIdPOP3.Disconnect;
  FreeAndNil(FIdPOP3);
  FreeAndNil(FIdSSL);
end;

procedure TfrmPOP3Client.DoLog(const aText: string);
begin
  TThread.Queue(nil, procedure
    begin
      if Assigned(memoLog) then
        memoLog.Lines.Add(aText);
    end);
end;

procedure TfrmPOP3Client.btnConnectClick(Sender: TObject);
begin
  memoLog.Lines.Clear;

  FIdSSL.SSLOptions.Mode := sslmUnassigned;
  FIdSSL.SSLOptions.VerifyMode := [];
  FIdSSL.SSLOptions.VerifyDepth := 0;

  case cboOpenSSLAPI.ItemIndex of
    0:
      FIdSSL.SSLOptions.APIVersion := sslvAPI_1_0;
    1:
      FIdSSL.SSLOptions.APIVersion := sslvAPI_1_1;
    2:
      FIdSSL.SSLOptions.APIVersion := sslvAPI_3_0;
  end;

  case cboTLSVersion.ItemIndex of
    0, 1:
      FIdSSL.SSLOptions.Method := sslvTLSv1;
    2:
      FIdSSL.SSLOptions.Method := sslvTLSv1_1;
    3:
      FIdSSL.SSLOptions.Method := sslvTLSv1_2;
    4:
      FIdSSL.SSLOptions.Method := sslvTLSv1_3;
  end;

  FIdPOP3.IOHandler := FIdSSL;
  FIdPOP3.Host := txtHost.Text;
  FIdPOP3.Port := StrToIntDef(txtPort.Text, 110);
  FIdPOP3.Username := txtUsername.Text;
  FIdPOP3.Password := txtPassword.Text;
  FIdPOP3.UseTLS := utUseExplicitTLS;

  DoLog('Connecting to ' + FIdPOP3.Host + ':' + IntToStr(FIdPOP3.Port) + '...');
  try
    FIdPOP3.Connect;
    FIdPOP3.Login;
    DoLog('Connected and logged in successfully.');
  except
    on E: Exception do
      DoLog('Connect error: ' + E.Message);
  end;
end;

procedure TfrmPOP3Client.btnDisconnectClick(Sender: TObject);
begin
  try
    FIdPOP3.Disconnect;
    DoLog('Disconnected.');
  except
    on E: Exception do
      DoLog('Disconnect error: ' + E.Message);
  end;
end;

procedure TfrmPOP3Client.btnCheckMessagesClick(Sender: TObject);
var
  vCount: Integer;
begin
  if not FIdPOP3.Connected then
  begin
    DoLog('Not connected.');
    Exit;
  end;
  try
    vCount := FIdPOP3.CheckMessages;
    DoLog('Messages on server: ' + IntToStr(vCount));
  except
    on E: Exception do
      DoLog('CheckMessages error: ' + E.Message);
  end;
end;

procedure TfrmPOP3Client.btnRetrieveMessageClick(Sender: TObject);
var
  vMsg: TIdMessage;
  vMsgNum: Integer;
begin
  if not FIdPOP3.Connected then
  begin
    DoLog('Not connected.');
    Exit;
  end;
  vMsgNum := StrToIntDef(txtMsgNum.Text, 1);
  vMsg := TIdMessage.Create(nil);
  try
    try
      FIdPOP3.Retrieve(vMsgNum, vMsg);
      DoLog('--- Message #' + IntToStr(vMsgNum) + ' ---');
      DoLog('Subject: ' + vMsg.Subject);
      DoLog('From: ' + vMsg.From.Text);
      DoLog('Date: ' + DateTimeToStr(vMsg.Date));
      DoLog('Body:');
      DoLog(vMsg.Body.Text);
      DoLog('--- End of Message ---');
    except
      on E: Exception do
        DoLog('Retrieve error: ' + E.Message);
    end;
  finally
    FreeAndNil(vMsg);
  end;
end;

procedure TfrmPOP3Client.btnDeleteMessageClick(Sender: TObject);
var
  vMsgNum: Integer;
begin
  if not FIdPOP3.Connected then
  begin
    DoLog('Not connected.');
    Exit;
  end;
  vMsgNum := StrToIntDef(txtMsgNum.Text, 1);
  try
    FIdPOP3.Delete(vMsgNum);
    DoLog('Message #' + IntToStr(vMsgNum) + ' marked for deletion.');
  except
    on E: Exception do
      DoLog('Delete error: ' + E.Message);
  end;
end;

end.
```

