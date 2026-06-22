# TIdFTP - Example

Full source of `fFtpClient.pas` from the **FtpClient** demo, which uses `TIdFTP`.

API reference: [TIdFTP](../reference/api/TIdFTP.md)
Source demo: `FtpClient` (file `fFtpClient.pas`)

```pascal
unit fFtpClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, IdIOHandler, IdIOHandlerSocket,
  IdIOHandlerStack, IdSSL, IdSSLOpenSSL, IdBaseComponent, IdComponent, IdGlobal,
  StdCtrls, IdSSLOpenSSLHeaders, IdTCPClient, IdExplicitTLSClientServerBase,
  IdFTP, IdTCPConnection, IdFTPCommon;

type
  TfrmFtpClient = class(TForm)
    IdFTP1: TIdFTP;
    IdSSLIOHandlerSocketOpenSSL1: TIdSSLIOHandlerSocketOpenSSL;
    btnConnect: TButton;
    btnDisconnect: TButton;
    txtHost: TEdit;
    lblHost: TLabel;
    lblPort: TLabel;
    txtPort: TEdit;
    memoLog: TMemo;
    btnList: TButton;
    cboOpenSSLAPI: TComboBox;
    cboTLSVersion: TComboBox;
    lblSSL: TLabel;
    txtUser: TEdit;
    Label1: TLabel;
    Label2: TLabel;
    txtPassword: TEdit;
    btnUpload: TButton;
    procedure btnConnectClick(Sender: TObject);
    procedure btnDisconnectClick(Sender: TObject);
    procedure btnListClick(Sender: TObject);
    procedure btnUploadClick(Sender: TObject);
    procedure IdSSLIOHandlerSocketOpenSSL1StatusInfoEx(ASender: TObject; const
        AsslSocket: PSSL; const AWhere, Aret: Integer; const AType, AMsg: string);
    procedure IdFTP1Connected(Sender: TObject);
    procedure IdFTP1Disconnected(Sender: TObject);
  private
    { Private declarations }
  public
    procedure DoLog(const aText: string);
    { Public declarations }
  end;

var
  frmftpClient: TfrmftpClient;

implementation

{$R *.dfm}

procedure TfrmftpClient.btnConnectClick(Sender: TObject);
begin
  case cboOpenSSLAPI.ItemIndex of
    0: IdSSLIOHandlerSocketOpenSSL1.SSLOptions.APIVersion := sslvAPI_1_0;
    1: IdSSLIOHandlerSocketOpenSSL1.SSLOptions.APIVersion := sslvAPI_1_1;
    2: IdSSLIOHandlerSocketOpenSSL1.SSLOptions.APIVersion := sslvAPI_3_0;
  end;

  case cboTLSVersion.ItemIndex of
    0,1: IdSSLIOHandlerSocketOpenSSL1.SSLOptions.Method := sslvTLSv1;
    2: IdSSLIOHandlerSocketOpenSSL1.SSLOptions.Method := sslvTLSv1_1;
    3: IdSSLIOHandlerSocketOpenSSL1.SSLOptions.Method := sslvTLSv1_2;
    4: IdSSLIOHandlerSocketOpenSSL1.SSLOptions.Method := sslvTLSv1_3;
  end;

  IdFTP1.Host := txtHost.Text;
  IdFTP1.Port := StrToInt(txtPort.Text);
  IdSSLIOHandlerSocketOpenSSL1.PassThrough := False;

  IdFTP1.Username := txtUser.Text;
  IdFTP1.Password := txtPassword.Text;

  IdFTP1.UseTLS := utUseExplicitTLS;
  IdFTP1.DataPortProtection := ftpdpsPrivate;
  IdFTP1.TransferType := ftBinary;
  IdFTP1.Passive := True;

  IdFTP1.Connect;
end;

procedure TfrmftpClient.btnDisconnectClick(Sender: TObject);
begin
  IdFTP1.Disconnect;
end;

procedure TfrmftpClient.btnListClick(Sender: TObject);
var
  oList: TStringList;
begin
  oList := TStringList.Create;
  Try
    IdFTP1.List(oList, '/', False);
    DoLog(oList.Text);
  Finally
    oList.Free;
  End;
end;

procedure TfrmFtpClient.btnUploadClick(Sender: TObject);
var
  oDialog: TOpenDialog;
begin
  oDialog := TOpenDialog.Create(nil);
  Try
    if oDialog.Execute then
      IdFTP1.Put(oDialog.FileName);
  Finally
    oDialog.Free;
  End;
end;

procedure TfrmftpClient.DoLog(const aText: string);
begin
  TThread.Queue(nil,
    procedure
    begin
	  if Assigned(memoLog) then
		memoLog.Lines.Add(aText);
    end);
end;

procedure TfrmftpClient.IdSSLIOHandlerSocketOpenSSL1StatusInfoEx(ASender: TObject;
    const AsslSocket: PSSL; const AWhere, Aret: Integer; const AType, AMsg:
    string);
begin
  DoLog(AMsg);
end;

procedure TfrmftpClient.IdFTP1Connected(Sender: TObject);
begin
  DoLog('#connected');
end;

procedure TfrmftpClient.IdFTP1Disconnected(Sender: TObject);
begin
  DoLog('#disconnected');
end;

end.
```

