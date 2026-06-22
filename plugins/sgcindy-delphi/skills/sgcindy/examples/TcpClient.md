# TcpClient

Featured demo. Full source of every unit.

Demo: `TcpClient`

### fTcpClient.pas

```pascal
unit fTcpClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, IdIOHandler, IdIOHandlerSocket,
  IdIOHandlerStack, IdSSL, IdSSLOpenSSL, IdBaseComponent, IdComponent, IdGlobal,
  IdTCPConnection, IdTCPClient, StdCtrls, IdSSLOpenSSLHeaders,
  IdThreadComponent, IdCTypes;

type
  TfrmTCPClient = class(TForm)
    IdTCPClient1: TIdTCPClient;
    IdSSLIOHandlerSocketOpenSSL1: TIdSSLIOHandlerSocketOpenSSL;
    btnConnect: TButton;
    btnDisconnect: TButton;
    txtHost: TEdit;
    lblHost: TLabel;
    lblPort: TLabel;
    txtPort: TEdit;
    memoLog: TMemo;
    btnSend: TButton;
    txtMessage: TEdit;
    IdThreadComponent1: TIdThreadComponent;
    cboOpenSSLAPI: TComboBox;
    cboTLSVersion: TComboBox;
    lblSSL: TLabel;
    procedure btnConnectClick(Sender: TObject);
    procedure btnDisconnectClick(Sender: TObject);
    procedure btnSendClick(Sender: TObject);
    procedure IdSSLIOHandlerSocketOpenSSL1Status(ASender: TObject; const AStatus:
        TIdStatus; const AStatusText: string);
    procedure IdSSLIOHandlerSocketOpenSSL1StatusInfo(const AMsg: string);
    procedure IdSSLIOHandlerSocketOpenSSL1StatusInfoEx(ASender: TObject; const
        AsslSocket: PSSL; const AWhere, Aret: Integer; const AType, AMsg: string);
    procedure IdTCPClient1Connected(Sender: TObject);
    procedure IdTCPClient1Disconnected(Sender: TObject);
    procedure IdThreadComponent1Run(Sender: TIdThreadComponent);
  private
    { Private declarations }
  public
    procedure DoLog(const aText: string);
    { Public declarations }
  end;

var
  frmTCPClient: TfrmTCPClient;

implementation

{$R *.dfm}

procedure TfrmTCPClient.btnConnectClick(Sender: TObject);
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

  IdTCPClient1.Host := txtHost.Text;
  IdTCPClient1.Port := StrToInt(txtPort.Text);
  IdSSLIOHandlerSocketOpenSSL1.PassThrough := False;

  IdTCPClient1.Connect;
end;

procedure TfrmTCPClient.btnDisconnectClick(Sender: TObject);
begin
  IdTCPClient1.Disconnect;
end;

procedure TfrmTCPClient.btnSendClick(Sender: TObject);
begin
  IdTCPClient1.IOHandler.WriteBufferOpen;
  Try
    IdTCPClient1.IOHandler.Write(ToBytes(txtMessage.Text));
    txtMessage.Text := '';
    IdTCPClient1.IOHandler.WriteBufferFlush;
  Finally
    IdTCPClient1.IOHandler.WriteBufferClose;
  End;
end;

procedure TfrmTCPClient.DoLog(const aText: string);
begin
  TThread.Queue(nil,
    procedure
    begin
	  if Assigned(memoLog) then
		memoLog.Lines.Add(aText);
    end);
end;

procedure TfrmTCPClient.IdSSLIOHandlerSocketOpenSSL1Status(ASender: TObject; const
    AStatus: TIdStatus; const AStatusText: string);
begin
  DoLog(AStatusText);
end;

procedure TfrmTCPClient.IdSSLIOHandlerSocketOpenSSL1StatusInfo(const AMsg: string);
begin
  DoLog(AMsg);
end;

procedure TfrmTCPClient.IdSSLIOHandlerSocketOpenSSL1StatusInfoEx(ASender: TObject;
    const AsslSocket: PSSL; const AWhere, Aret: Integer; const AType, AMsg:
    string);
begin
  DoLog(AMsg);
end;

procedure TfrmTCPClient.IdTCPClient1Connected(Sender: TObject);
begin
  DoLog('#connected');

  IdThreadComponent1.Active := True;
end;

procedure TfrmTCPClient.IdTCPClient1Disconnected(Sender: TObject);
begin
  DoLog('#disconnected');
  IdThreadComponent1.Stop;
end;

procedure TfrmTCPClient.IdThreadComponent1Run(Sender: TIdThreadComponent);
var
    vText : string;
begin
  // ... read message from server
  Try
    vText := IdTCPClient1.IOHandler.ReadLn();

    // ... messages log
    DoLog('#received: ' + vText);
  Except
    // nothing
  End;
end;

end.
```

