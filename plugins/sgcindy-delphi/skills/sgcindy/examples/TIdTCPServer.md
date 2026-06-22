# TIdTCPServer - Example

Full source of `fTcpServer.pas` from the **TcpServer** demo, which uses `TIdTCPServer`.

API reference: [TIdTCPServer](../reference/api/TIdTCPServer.md)
Source demo: `TcpServer` (file `fTcpServer.pas`)

```pascal
unit fTcpServer;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, IdIOHandler, IdIOHandlerSocket,
  IdIOHandlerStack, IdSSL, IdSSLOpenSSL, IdBaseComponent, IdComponent, IdGlobal,
  IdTCPConnection, IdTCPServer, StdCtrls, IdSSLOpenSSLHeaders,
  IdContext, IdServerIOHandler, IdCustomTCPServer;

type
  TfrmTCPServer = class(TForm)
    btnStart: TButton;
    btnStop: TButton;
    lblPort: TLabel;
    txtPort: TEdit;
    memoLog: TMemo;
    cboOpenSSLAPI: TComboBox;
    cboTLSVersion: TComboBox;
    lblSSL: TLabel;
    IdTCPServer1: TIdTCPServer;
    IdServerIOHandlerSSLOpenSSL1: TIdServerIOHandlerSSLOpenSSL;
    txtCertificate: TEdit;
    txtKey: TEdit;
    Label1: TLabel;
    Label2: TLabel;
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure IdServerIOHandlerSSLOpenSSL1StatusInfoEx(ASender: TObject; const
        AsslSocket: PSSL; const AWhere, Aret: Integer; const AType, AMsg: string);
    procedure IdSSLIOHandlerSocketOpenSSL1Status(ASender: TObject; const AStatus:
        TIdStatus; const AStatusText: string);
    procedure IdSSLIOHandlerSocketOpenSSL1StatusInfo(const AMsg: string);
    procedure IdSSLIOHandlerSocketOpenSSL1StatusInfoEx(ASender: TObject; const
        AsslSocket: PSSL; const AWhere, Aret: Integer; const AType, AMsg: string);
    procedure IdTCPServer1Connect(AContext: TIdContext);
    procedure IdTCPServer1Disconnect(AContext: TIdContext);
    procedure IdTCPServer1Exception(AContext: TIdContext; AException: Exception);
    procedure IdTCPServer1Execute(AContext: TIdContext);
    procedure IdTCPServer1Status(ASender: TObject; const AStatus: TIdStatus; const
        AStatusText: string);
  private
    { Private declarations }
  public
    procedure DoLog(const aText: string);
    { Public declarations }
  end;

var
  frmTCPServer: TfrmTCPServer;

implementation

{$R *.dfm}

procedure TfrmTCPServer.btnStartClick(Sender: TObject);
begin
  case cboOpenSSLAPI.ItemIndex of
    0: IdServerIOHandlerSSLOpenSSL1.SSLOptions.APIVersion := sslvAPI_1_0;
    1: IdServerIOHandlerSSLOpenSSL1.SSLOptions.APIVersion := sslvAPI_1_1;
    2: IdServerIOHandlerSSLOpenSSL1.SSLOptions.APIVersion := sslvAPI_3_0;
  end;

  case cboTLSVersion.ItemIndex of
    0,1: IdServerIOHandlerSSLOpenSSL1.SSLOptions.Method := sslvTLSv1;
    2: IdServerIOHandlerSSLOpenSSL1.SSLOptions.Method := sslvTLSv1_1;
    3: IdServerIOHandlerSSLOpenSSL1.SSLOptions.Method := sslvTLSv1_2;
    4: IdServerIOHandlerSSLOpenSSL1.SSLOptions.Method := sslvTLSv1_3;
  end;

  IdServerIOHandlerSSLOpenSSL1.SSLOptions.Mode := sslmServer;
  IdServerIOHandlerSSLOpenSSL1.SSLOptions.VerifyDepth := 0;
  IdServerIOHandlerSSLOpenSSL1.SSLOptions.CertFile := txtCertificate.Text;
  IdServerIOHandlerSSLOpenSSL1.SSLOptions.KeyFile := txtKey.Text;

  IdTCPServer1.DefaultPort := StrToInt(txtPort.Text);

  IdTCPServer1.Active := True;

  DoLog('#started');
end;

procedure TfrmTCPServer.btnStopClick(Sender: TObject);
begin
  IdTCPServer1.Active := False;

  DoLog('#stopped');
end;

procedure TfrmTCPServer.DoLog(const aText: string);
begin
  TThread.Queue(nil,
    procedure
    begin
	  if Assigned(memoLog) then
		memoLog.Lines.Add(aText);
    end);
end;

procedure TfrmTCPServer.IdServerIOHandlerSSLOpenSSL1StatusInfoEx(ASender:
    TObject; const AsslSocket: PSSL; const AWhere, Aret: Integer; const AType,
    AMsg: string);
begin
  DoLog('status: ' + AMsg);
end;

procedure TfrmTCPServer.IdSSLIOHandlerSocketOpenSSL1Status(ASender: TObject; const
    AStatus: TIdStatus; const AStatusText: string);
begin
  DoLog(AStatusText);
end;

procedure TfrmTCPServer.IdSSLIOHandlerSocketOpenSSL1StatusInfo(const AMsg: string);
begin
  DoLog(AMsg);
end;

procedure TfrmTCPServer.IdSSLIOHandlerSocketOpenSSL1StatusInfoEx(ASender: TObject;
    const AsslSocket: PSSL; const AWhere, Aret: Integer; const AType, AMsg:
    string);
begin
  DoLog(AMsg);
end;

procedure TfrmTCPServer.IdTCPServer1Connect(AContext: TIdContext);
begin
  DoLog('#connected');
  TIdSSLIOHandlerSocketBase(AContext.Connection.IOHandler).PassThrough := false;
end;

procedure TfrmTCPServer.IdTCPServer1Disconnect(AContext: TIdContext);
begin
  DoLog('#disconnected');
end;

procedure TfrmTCPServer.IdTCPServer1Exception(AContext: TIdContext; AException:
    Exception);
begin
  DoLog('#exception: ' + AException.message);
end;

procedure TfrmTCPServer.IdTCPServer1Execute(AContext: TIdContext);
var
  vMessage: string;
begin

  if AContext.Connection.IOHandler.InputBufferIsEmpty then
    AContext.Connection.IOHandler.CheckForDataOnSource(10)
  else
  begin
    vMessage := AContext.Connection.IOHandler.InputBuffer.AsString;
    AContext.Connection.IOHandler.InputBuffer.Clear;
    DoLog('#received: ' + vMessage);
    AContext.Connection.IOHandler.WriteLn(vMessage)
  end;
end;

procedure TfrmTCPServer.IdTCPServer1Status(ASender: TObject; const AStatus:
    TIdStatus; const AStatusText: string);
begin
  DoLog(AStatusText);
end;

end.
```

