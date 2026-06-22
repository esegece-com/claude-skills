# TsgcWSPClient_sgc - Example

Full source of `uClientPROTOCOL.pas` from the **02.WebSocket_Protocols/01.SGC_Generic_PubSub_Protocol** demo, which uses `TsgcWSPClient_sgc`.

API reference: [TsgcWSPClient_sgc](../reference/api/TsgcWSPClient_sgc.md)
Source demo: `02.WebSocket_Protocols/01.SGC_Generic_PubSub_Protocol` (file `uClientPROTOCOL.pas`)

```pascal
unit uClientPROTOCOL;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, sgcWebSocket_Classes, sgcWebSocket_Client, sgcWebSocket, StdCtrls,
  ExtCtrls, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocol_WAMP_Client, sgcWebSocket_Protocols,
  sgcWebSocket_Protocol_sgc_Client, sgcWebSocket_Classes_Indy,
  sgcWebSocket_Types, sgcBase_Classes, sgcSocket_Classes, sgcTCP_Classes;

type
  TfrmClientPROTOCOL = class(TForm)
    pnlClient: TPanel;
    memoLog: TMemo;
    WSClient: TsgcWebSocketClient;
    btnSubscribe: TButton;
    pnlClientActive: TPanel;
    btnStart: TButton;
    btnStop: TButton;
    pnlClientOptions: TPanel;
    Label3: TLabel;
    Label4: TLabel;
    chkCompressed: TCheckBox;
    chkTLS: TCheckBox;
    txtHost: TEdit;
    Label5: TLabel;
    Default: TLabel;
    txtDefaultPort: TEdit;
    chkProxy: TCheckBox;
    Label7: TLabel;
    txtProxyUsername: TEdit;
    txtProxyPassword: TEdit;
    Label8: TLabel;
    Label9: TLabel;
    txtProxyHost: TEdit;
    txtProxyPort: TEdit;
    Label10: TLabel;
    btnUnsubscribe: TButton;
    txtChannel: TEdit;
    btnNotify: TButton;
    txtNotify: TEdit;
    btnRPC: TButton;
    txtRPCID: TEdit;
    txtRPCMethod: TEdit;
    txtRPCParams: TEdit;
    btnPublish: TButton;
    txtPublishChannel: TEdit;
    txtPublishMessage: TEdit;
    Label1: TLabel;
    Label2: TLabel;
    Label11: TLabel;
    Label12: TLabel;
    WSPPROTOCOL: TsgcWSPClient_sgc;
    btnGetSession: TButton;
    Label13: TLabel;
    btnStartTransaction: TButton;
    btnCommit: TButton;
    btnRollBack: TButton;
    Label14: TLabel;
    txtTransactionChannel: TEdit;
    cboQoSLevel: TComboBox;
    Label15: TLabel;
    cboQueueLevel: TComboBox;
    btnUnSubscribeAll: TButton;
    procedure btnCommitClick(Sender: TObject);
    procedure btnGetSessionClick(Sender: TObject);
    procedure btnNotifyClick(Sender: TObject);
    procedure btnSubscribeClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure btnUnsubscribeClick(Sender: TObject);
    procedure btnRPCClick(Sender: TObject);
    procedure btnPublishClick(Sender: TObject);
    procedure btnRollBackClick(Sender: TObject);
    procedure btnStartTransactionClick(Sender: TObject);
    procedure btnUnSubscribeAllClick(Sender: TObject);
    procedure WSPPROTOCOLConnect(Connection: TsgcWSConnection);
    procedure WSPPROTOCOLDisconnect(Connection: TsgcWSConnection; Code:
        Integer);
    procedure WSPPROTOCOLError(Connection: TsgcWSConnection; const Error:
        string);
    procedure WSPPROTOCOLMessage(Connection: TsgcWSConnection; const Text:
        string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSPPROTOCOLAcknowledgment(Connection: TsgcWSConnection; const Id:
        string);
    procedure WSPPROTOCOLEvent(Connection: TsgcWSConnection; const Channel, Text:
        string);
    procedure WSPPROTOCOLRPCError(Connection: TsgcWSConnection; Id: string;
        ErrorCode: Integer; ErrorMessage, ErrorData: string);
    procedure WSPPROTOCOLRPCResult(Connection: TsgcWSConnection; Id, Result:
        string);
    procedure WSPPROTOCOLSession(Connection: TsgcWSConnection; Guid: string);
    procedure WSPPROTOCOLSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
    procedure WSPPROTOCOLUnSubscription(Connection: TsgcWSConnection; const
        Subscription: string);
  private
    { Private declarations }
  public
    { Public declarations }
  end;

var
  frmClientPROTOCOL: TfrmClientPROTOCOL;

implementation

uses
  sgcJSON;

{$R *.dfm}

procedure TfrmClientPROTOCOL.btnCommitClick(Sender: TObject);
begin
  WSPPROTOCOL.Commit(txtTransactionChannel.Text);
end;

procedure TfrmClientPROTOCOL.btnGetSessionClick(Sender: TObject);
begin
  WSPProtocol.GetSession;
end;

procedure TfrmClientPROTOCOL.btnNotifyClick(Sender: TObject);
begin
  WSPProtocol.Notify(txtNotify.Text);
end;

procedure TfrmClientPROTOCOL.btnSubscribeClick(Sender: TObject);
begin
  WSPPROTOCOL.Subscribe(txtChannel.text);
end;

procedure TfrmClientPROTOCOL.btnStartClick(Sender: TObject);
begin
  case cboQoSLevel.ItemIndex of
    0: WSPPROTOCOL.QoS.Level := qosLevel0;
    1: WSPPROTOCOL.QoS.Level := qosLevel1;
    2: WSPPROTOCOL.QoS.Level := qosLevel2;
  end;

  WSClient.Port := StrToInt(txtDefaultPort.Text);
  WSClient.Host := txtHost.Text;

  WSClient.TLS := chkTLS.Checked;

  WSClient.Proxy.Enabled := chkProxy.Checked;
  WSClient.Proxy.Username := txtProxyUsername.Text;
  WSClient.Proxy.Password := txtProxyPassword.Text;
  WSClient.Proxy.Host := txtProxyHost.Text;
  if txtProxyPort.Text <> '' then
    WSClient.Proxy.Port := StrToInt(txtProxyPort.Text);

  WSClient.Extensions.DeflateFrame.Enabled := chkCompressed.Checked;

  // ... active
  WSClient.Active := True;
  if WSClient.Active then
    pnlClientOptions.Enabled := False;
end;

procedure TfrmClientPROTOCOL.btnStopClick(Sender: TObject);
begin
  WSClient.Active := False;

  if not WSClient.Active then
    pnlClientOptions.Enabled := True;
end;

procedure TfrmClientPROTOCOL.btnUnsubscribeClick(Sender: TObject);
begin
  WSPPROTOCOL.UnSubscribe(txtChannel.text);
end;

procedure TfrmClientPROTOCOL.btnRPCClick(Sender: TObject);
begin
  WSPPROTOCOL.RPC(txtRPCID.Text, txtRPCMethod.Text, txtRPCParams.Text);
end;

procedure TfrmClientPROTOCOL.btnPublishClick(Sender: TObject);
begin
  WSPPROTOCOL.Publish(txtPublishMessage.Text, txtPublishChannel.Text, '', TwsQueue(cboQueueLevel.ItemIndex));
end;

procedure TfrmClientPROTOCOL.btnRollBackClick(Sender: TObject);
begin
  WSPPROTOCOL.RollBack(txtTransactionChannel.Text);
end;

procedure TfrmClientPROTOCOL.btnStartTransactionClick(Sender: TObject);
begin
  WSPPROTOCOL.StartTransaction(txtTransactionChannel.Text);
end;

procedure TfrmClientPROTOCOL.btnUnSubscribeAllClick(Sender: TObject);
begin
  WSPPROTOCOL.UnSubscribeAll;
end;

procedure TfrmClientPROTOCOL.WSPPROTOCOLConnect(Connection:
    TsgcWSConnection);
begin
  memoLog.Lines.Add('#connected');
  chkTLS.Enabled := False;
  chkCompressed.Enabled := False;
end;

procedure TfrmClientPROTOCOL.WSPPROTOCOLDisconnect(Connection:
    TsgcWSConnection; Code: Integer);
begin
  memoLog.Lines.Add('#disconnected (' + IntToStr(Code) + ')');
  chkTLS.Enabled := True;
  chkCompressed.Enabled := True;
end;

procedure TfrmClientPROTOCOL.WSPPROTOCOLError(Connection: TsgcWSConnection;
    const Error: string);
begin
  memoLog.Lines.Add('#error: ' + Error);
end;

procedure TfrmClientPROTOCOL.WSPPROTOCOLMessage(Connection:
    TsgcWSConnection; const Text: string);
begin
  memoLog.Lines.Add(Text);
end;

procedure TfrmClientPROTOCOL.WSClientException(Connection: TsgcWSConnection; E:
    Exception);
begin
  MemoLog.Lines.Add('#exception:' + E.Message);
end;

procedure TfrmClientPROTOCOL.WSPPROTOCOLAcknowledgment(Connection:
    TsgcWSConnection; const Id: string);
begin
  memoLog.Lines.Add('#acknowledgment: ' + Id);
end;

procedure TfrmClientPROTOCOL.WSPPROTOCOLEvent(Connection: TsgcWSConnection;
    const Channel, Text: string);
begin
  memoLog.Lines.Add('#Event: ' + Channel + ' - ' + Text);
end;

procedure TfrmClientPROTOCOL.WSPPROTOCOLRPCError(Connection: TsgcWSConnection;
    Id: string; ErrorCode: Integer; ErrorMessage, ErrorData: string);
begin
  memoLog.Lines.Add('#RPC Error: ' + Id + ' - ' + IntToStr(ErrorCode) + ' - ' + ErrorMessage + ' - ' + ErrorData);
end;

procedure TfrmClientPROTOCOL.WSPPROTOCOLRPCResult(Connection: TsgcWSConnection;
    Id, Result: string);
begin
  memoLog.Lines.Add('#RPC Result: ' + Id + ' - ' + Result);
end;

procedure TfrmClientPROTOCOL.WSPPROTOCOLSession(Connection: TsgcWSConnection;
    Guid: string);
begin
  memoLog.Lines.Add('#session: ' + Guid);
end;

procedure TfrmClientPROTOCOL.WSPPROTOCOLSubscription(Connection:
    TsgcWSConnection; const Subscription: string);
begin
  memoLog.Lines.Add('#subscribed: ' + Subscription);
end;

procedure TfrmClientPROTOCOL.WSPPROTOCOLUnSubscription(Connection:
    TsgcWSConnection; const Subscription: string);
begin
  memoLog.Lines.Add('#unsubscribed: ' + Subscription);
end;

end.
```

