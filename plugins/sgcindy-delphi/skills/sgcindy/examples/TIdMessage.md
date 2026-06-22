# TIdMessage - Example

Full source of `fIMAP4Client.pas` from the **IMAP4Client** demo, which uses `TIdMessage`.

API reference: [TIdMessage](../reference/api/TIdMessage.md)
Source demo: `IMAP4Client` (file `fIMAP4Client.pas`)

```pascal
{ ***************************************************************************
  sgcIndy IMAP4 Client Demo

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit fIMAP4Client;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls, IdIOHandler, IdIOHandlerSocket,
  IdIOHandlerStack, IdSSL, IdSSLOpenSSL, IdSSLOpenSSLHeaders,
  IdBaseComponent, IdComponent, IdTCPConnection, IdTCPClient,
  IdExplicitTLSClientServerBase, IdIMAP4, IdMessage;

type
  TfrmIMAP4Client = class(TForm)
    lblHost: TLabel;
    txtHost: TEdit;
    lblPort: TLabel;
    txtPort: TEdit;
    lblUsername: TLabel;
    txtUsername: TEdit;
    lblPassword: TLabel;
    txtPassword: TEdit;
    lblOpenSSLAPI: TLabel;
    cboOpenSSLAPI: TComboBox;
    lblTLSVersion: TLabel;
    cboTLSVersion: TComboBox;
    btnConnect: TButton;
    btnDisconnect: TButton;
    lblMailbox: TLabel;
    txtMailbox: TEdit;
    btnSelectMailbox: TButton;
    btnListMailboxes: TButton;
    lblMsgNum: TLabel;
    txtMsgNum: TEdit;
    btnFetchMessage: TButton;
    memoLog: TMemo;
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure btnConnectClick(Sender: TObject);
    procedure btnDisconnectClick(Sender: TObject);
    procedure btnListMailboxesClick(Sender: TObject);
    procedure btnSelectMailboxClick(Sender: TObject);
    procedure btnFetchMessageClick(Sender: TObject);
  private
    FIMAP4: TIdIMAP4;
    FSSLHandler: TIdSSLIOHandlerSocketOpenSSL;
    procedure DoLog(const aMessage: string);
  public
  end;

var
  frmIMAP4Client: TfrmIMAP4Client;

implementation

{$R *.dfm}

procedure TfrmIMAP4Client.FormCreate(Sender: TObject);
begin
  FSSLHandler := TIdSSLIOHandlerSocketOpenSSL.Create(nil);
  FIMAP4 := TIdIMAP4.Create(nil);
  FIMAP4.IOHandler := FSSLHandler;
end;

procedure TfrmIMAP4Client.FormDestroy(Sender: TObject);
begin
  if FIMAP4.Connected then
    FIMAP4.Disconnect;
  FreeAndNil(FIMAP4);
  FreeAndNil(FSSLHandler);
end;

procedure TfrmIMAP4Client.DoLog(const aMessage: string);
begin
  TThread.Queue(nil, procedure
    begin
      memoLog.Lines.Add(FormatDateTime('hh:nn:ss', Now) + ' ' + aMessage);
    end);
end;

procedure TfrmIMAP4Client.btnConnectClick(Sender: TObject);
begin
  try
    FIMAP4.Host := txtHost.Text;
    FIMAP4.Port := StrToIntDef(txtPort.Text, 143);
    FIMAP4.Username := txtUsername.Text;
    FIMAP4.Password := txtPassword.Text;

    case cboOpenSSLAPI.ItemIndex of
      0:
        FSSLHandler.SSLOptions.SSLVersions :=
          [sslvTLSv1, sslvTLSv1_1, sslvTLSv1_2];
      1:
        FSSLHandler.SSLOptions.SSLVersions := [sslvTLSv1_2];
    end;

    case cboTLSVersion.ItemIndex of
      0:
        FIMAP4.UseTLS := utNoTLSSupport;
      1:
        FIMAP4.UseTLS := utUseExplicitTLS;
      2:
        FIMAP4.UseTLS := utUseImplicitTLS;
    else
      FIMAP4.UseTLS := utUseExplicitTLS;
    end;

    FIMAP4.Connect;
    DoLog('Connected to ' + FIMAP4.Host + ':' + IntToStr(FIMAP4.Port));
  except
    on E: Exception do
      DoLog('Connect error: ' + E.Message);
  end;
end;

procedure TfrmIMAP4Client.btnDisconnectClick(Sender: TObject);
begin
  try
    FIMAP4.Disconnect;
    DoLog('Disconnected.');
  except
    on E: Exception do
      DoLog('Disconnect error: ' + E.Message);
  end;
end;

procedure TfrmIMAP4Client.btnListMailboxesClick(Sender: TObject);
var
  oList: TStringList;
  i: Integer;
begin
  oList := TStringList.Create;
  try
    try
      FIMAP4.ListMailBoxes(oList);
      DoLog('--- Mailboxes ---');
      for i := 0 to oList.Count - 1 do
        DoLog('  ' + oList[i]);
      DoLog('Total: ' + IntToStr(oList.Count) + ' mailbox(es)');
    except
      on E: Exception do
        DoLog('ListMailboxes error: ' + E.Message);
    end;
  finally
    oList.Free;
  end;
end;

procedure TfrmIMAP4Client.btnSelectMailboxClick(Sender: TObject);
begin
  try
    FIMAP4.SelectMailBox(txtMailbox.Text);
    DoLog('Selected mailbox: ' + txtMailbox.Text + ' (' +
      IntToStr(FIMAP4.MailBox.TotalMsgs) + ' messages)');
  except
    on E: Exception do
      DoLog('SelectMailbox error: ' + E.Message);
  end;
end;

procedure TfrmIMAP4Client.btnFetchMessageClick(Sender: TObject);
var
  oMsg: TIdMessage;
  vMsgNum: Integer;
begin
  vMsgNum := StrToIntDef(txtMsgNum.Text, 0);
  if vMsgNum <= 0 then
  begin
    DoLog('Invalid message number.');
    Exit;
  end;

  oMsg := TIdMessage.Create(nil);
  try
    try
      FIMAP4.Retrieve(vMsgNum, oMsg);
      DoLog('--- Message #' + IntToStr(vMsgNum) + ' ---');
      DoLog('  Subject: ' + oMsg.Subject);
      DoLog('  From: ' + oMsg.From.Text);
      DoLog('  Date: ' + DateTimeToStr(oMsg.Date));
    except
      on E: Exception do
        DoLog('FetchMessage error: ' + E.Message);
    end;
  finally
    oMsg.Free;
  end;
end;

end.
```

