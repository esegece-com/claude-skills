# TsgcTCPClient - Example

Full source of `uClientAMQP.pas` from the **02.WebSocket_Protocols/10.AMQP_Client** demo, which uses `TsgcTCPClient`.

API reference: [TsgcTCPClient](../reference/api/TsgcTCPClient.md)
Source demo: `02.WebSocket_Protocols/10.AMQP_Client` (file `uClientAMQP.pas`)

```pascal
unit uClientAMQP;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ComCtrls, Menus, StdCtrls, ExtCtrls,
  sgcWebSocket_Protocol_Base_Client, sgcWebSocket_Classes, sgcWebSocket_Client,
  sgcWebSocket,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_Protocol_AMQP_Client, sgcAMQP_Classes, sgcBase_Classes,
  sgcSocket_Classes, sgcTCP_Classes, sgcWebSocket_Classes_SyncObjs;

type
  TfrmClientAMQP = class(TForm)
    pnlClient: TPanel;
    memoLog: TMemo;
    WSClient: TsgcWebSocketClient;
    pnlClientActive: TPanel;
    btnStart: TButton;
    btnStop: TButton;
    pnlClientOptions: TPanel;
    Label3: TLabel;
    Label4: TLabel;
    chkTLS: TCheckBox;
    txtHost: TEdit;
    Label5: TLabel;
    Default: TLabel;
    txtDefaultPort: TEdit;
    Label6: TLabel;
    txtSSLPort: TEdit;
    chkProxy: TCheckBox;
    Label7: TLabel;
    txtProxyUsername: TEdit;
    txtProxyPassword: TEdit;
    Label8: TLabel;
    Label9: TLabel;
    txtProxyHost: TEdit;
    txtProxyPort: TEdit;
    Label10: TLabel;
    AMQP: TsgcWSPClient_AMQP;
    txtUser: TEdit;
    txtPassword: TEdit;
    Label11: TLabel;
    Label13: TLabel;
    PageControl1: TPageControl;
    tabChannelExchangesQueues: TTabSheet;
    listChannels: TListView;
    btnChannelOpen: TButton;
    txtChannelName: TEdit;
    popupChannels: TPopupMenu;
    ChannelClose1: TMenuItem;
    ChannelEnable1: TMenuItem;
    ChannelDisable1: TMenuItem;
    listExchanges: TListView;
    btnExchangeDeclare: TButton;
    txtExchangeName: TEdit;
    Label14: TLabel;
    Label15: TLabel;
    chkExchangePassive: TCheckBox;
    chkExchangeDurable: TCheckBox;
    chkExchangeAutoDelete: TCheckBox;
    chkExchangeInternal: TCheckBox;
    chkExchangeNoWait: TCheckBox;
    txtExchangeType: TEdit;
    popupExchanges: TPopupMenu;
    DeleteExchange1: TMenuItem;
    Label16: TLabel;
    listQueues: TListView;
    btnQueueDeclare: TButton;
    txtQueueName: TEdit;
    chkQueuePassive: TCheckBox;
    chkQueueDurable: TCheckBox;
    chkQueueExclusive: TCheckBox;
    chkQueueAutoDelete: TCheckBox;
    chkQueueNoWait: TCheckBox;
    popupQueues: TPopupMenu;
    DeleteQueue1: TMenuItem;
    btnQueueBind: TButton;
    txtQueueRoutingKey: TEdit;
    btnQueueUnBind: TButton;
    btnQueuePurge: TButton;
    PageControl2: TPageControl;
    tabQoS: TTabSheet;
    btnSetQoS: TButton;
    txtQoSPrefetchSize: TEdit;
    Label17: TLabel;
    txtQoSPrefetchCount: TEdit;
    Label18: TLabel;
    chkQoSGlobal: TCheckBox;
    tabConsume: TTabSheet;
    chkConsumeNoLocal: TCheckBox;
    chkConsumeExclusive: TCheckBox;
    chkConsumeNoWait: TCheckBox;
    chkConsumeNoAck: TCheckBox;
    txtConsumeConsumerTag: TEdit;
    Label19: TLabel;
    btnConsume: TButton;
    btnCancelConsume: TButton;
    tabPublish: TTabSheet;
    txtPublishMessage: TEdit;
    btnPublishMessage: TButton;
    Label1: TLabel;
    txtRoutingKey: TEdit;
    chkMandatory: TCheckBox;
    chkImmediate: TCheckBox;
    tabReceiveMessages: TTabSheet;
    btnGetMessage: TButton;
    chkGetMessageNoWait: TCheckBox;
    btnAckMessage: TButton;
    txtDeliveryTag: TEdit;
    btnRejectMessage: TButton;
    Label2: TLabel;
    chkAckMultiple: TCheckBox;
    chkRejectRequeue: TCheckBox;
    btnRecoverMessage: TButton;
    chkRecoverRequeue: TCheckBox;
    btnRecoverAsyncMessage: TButton;
    tabTransactions: TTabSheet;
    btnSelectTransaction: TButton;
    btnCommitTransaction: TButton;
    btnRollbackTransaction: TButton;
    procedure FormDestroy(Sender: TObject);
    procedure AMQPAMQPAuthentication(Sender: TObject;
      aMechanisms: TsgcAMQPAuthentications;
      var Mechanism: TsgcAMQPAuthentication; var User, Password: string);
    procedure AMQPAMQPBasicCancelConsume(Sender: TObject;
      const aChannel, aConsumerTag: string);
    procedure AMQPAMQPBasicConsume(Sender: TObject;
      const aChannel, aConsumerTag: string);
    procedure AMQPAMQPBasicDeliver(Sender: TObject; const aChannel: string;
      const aDeliver: TsgcAMQPFramePayload_Method_BasicDeliver;
      const aContent: TsgcAMQPMessageContent);
    procedure AMQPAMQPBasicGetEmpty(Sender: TObject; const aChannel: string);
    procedure AMQPAMQPBasicGetOk(Sender: TObject; const aChannel: string;
      const aGetOk: TsgcAMQPFramePayload_Method_BasicGetOk;
      const aContent: TsgcAMQPMessageContent);
    procedure AMQPAMQPBasicQoS(Sender: TObject; const aChannel: string;
      const aQoS: TsgcAMQPFramePayload_Method_BasicQoS);
    procedure AMQPAMQPBasicRecoverOk(Sender: TObject; const aChannel: string);
    procedure AMQPAMQPBasicReturn(Sender: TObject; const aChannel: string;
      const aReturn: TsgcAMQPFramePayload_Method_BasicReturn;
      const aContent: TsgcAMQPMessageContent);
    procedure AMQPAMQPChannelClose(Sender: TObject; const aChannel: string;
      const aChannelClose: TsgcAMQPFramePayload_Method_ChannelClose;
      aAck: Boolean);
    procedure AMQPAMQPChannelOpen(Sender: TObject; const aChannel: string);
    procedure AMQPAMQPConnect(Sender: TObject);
    procedure AMQPAMQPDisconnect(Sender: TObject;
      const aClose: TsgcAMQPFramePayload_Method_ConnectionClose; aAck: Boolean);
    procedure AMQPAMQPException(Sender: TObject; E: Exception);
    procedure AMQPAMQPExchangeDeclare(Sender: TObject;
      const aChannel, aExchange: string);
    procedure AMQPAMQPExchangeDelete(Sender: TObject;
      const aChannel, aExchange: string);
    procedure AMQPAMQPHeartBeat(Sender: TObject);
    procedure AMQPAMQPQueueBind(Sender: TObject;
      const aChannel, aQueue, aExchange: string);
    procedure AMQPAMQPQueueDeclare(Sender: TObject;
      const aChannel, aQueue: string; aMessageCount, aConsumerCount: Integer);
    procedure AMQPAMQPQueueDelete(Sender: TObject;
      const aChannel, aQueue: string; aMessageCount: Integer);
    procedure AMQPAMQPQueuePurge(Sender: TObject;
      const aChannel, aQueue: string; aMessageCount: Integer);
    procedure AMQPAMQPQueueUnBind(Sender: TObject;
      const aChannel, aQueue, aExchange: string);
    procedure AMQPAMQPTransactionOk(Sender: TObject; const aChannel: string;
      aTransaction: TsgcAMQPTransaction);
    procedure btnAckMessageClick(Sender: TObject);
    procedure btnChannelOpenClick(Sender: TObject);
    procedure btnConsumeClick(Sender: TObject);
    procedure btnExchangeDeclareClick(Sender: TObject);
    procedure btnQueueBindClick(Sender: TObject);
    procedure btnQueueDeclareClick(Sender: TObject);
    procedure btnQueueDeleteClick(Sender: TObject);
    procedure btnQueuePurgeClick(Sender: TObject);
    procedure btnQueueUnBindClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure btnSetQoSClick(Sender: TObject);
    procedure btnCancelConsumeClick(Sender: TObject);
    procedure btnCommitTransactionClick(Sender: TObject);
    procedure btnGetMessageClick(Sender: TObject);
    procedure btnPublishMessageClick(Sender: TObject);
    procedure btnRecoverAsyncMessageClick(Sender: TObject);
    procedure btnRejectMessageClick(Sender: TObject);
    procedure btnRecoverMessageClick(Sender: TObject);
    procedure btnRollbackTransactionClick(Sender: TObject);
    procedure btnSelectTransactionClick(Sender: TObject);
    procedure ChannelClose1Click(Sender: TObject);
    procedure ChannelDisable1Click(Sender: TObject);
    procedure ChannelEnable1Click(Sender: TObject);
    procedure DeleteExchange1Click(Sender: TObject);
    procedure DeleteQueue1Click(Sender: TObject);
    procedure listChannelsClick(Sender: TObject);
    procedure listExchangesClick(Sender: TObject);
    procedure listQueuesClick(Sender: TObject);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
  private
    FExchanges: TStringList;
    FQueues: TStringList;
    procedure DoListExchanges(const aChannel: string);
    procedure DoListQueues(const aChannel: string);
    procedure DoLog(const aText: string);
    function GetExchanges: TStringList;
    function GetQueues: TStringList;
  public
    property Exchanges: TStringList read GetExchanges write FExchanges;
    property Queues: TStringList read GetQueues write FQueues;
  end;

var
  frmClientAMQP: TfrmClientAMQP;

implementation

{$R *.dfm}

procedure TfrmClientAMQP.FormDestroy(Sender: TObject);
begin
  FreeAndNil(FExchanges);
  FreeAndNil(FQueues);
end;

procedure TfrmClientAMQP.AMQPAMQPAuthentication(Sender: TObject;
  aMechanisms: TsgcAMQPAuthentications; var Mechanism: TsgcAMQPAuthentication;
  var User, Password: string);
begin
  User := txtUser.text;
  Password := txtPassword.Text;
end;

procedure TfrmClientAMQP.AMQPAMQPBasicCancelConsume(Sender: TObject;
  const aChannel, aConsumerTag: string);
begin
  DoLog('#AMQP_basic_cancel_consume: ' + aChannel + ' ' + aConsumerTag);
end;

procedure TfrmClientAMQP.AMQPAMQPBasicConsume(Sender: TObject;
  const aChannel, aConsumerTag: string);
begin
  DoLog('#AMQP_basic_consume: ' + aChannel + ' ' + aConsumerTag);
end;

procedure TfrmClientAMQP.AMQPAMQPBasicDeliver(Sender: TObject;
  const aChannel: string;
  const aDeliver: TsgcAMQPFramePayload_Method_BasicDeliver;
  const aContent: TsgcAMQPMessageContent);
begin
  DoLog('#AMQP_basic_deliver: ' + aChannel + ' ' + aDeliver.ConsumerTag + ' ' +
    ' ' + aContent.Body.AsString);
end;

procedure TfrmClientAMQP.AMQPAMQPBasicGetEmpty(Sender: TObject;
  const aChannel: string);
begin
  DoLog('#AMQP_basic_GetEmpty: ' + aChannel);
end;

procedure TfrmClientAMQP.AMQPAMQPBasicGetOk(Sender: TObject;
  const aChannel: string; const aGetOk: TsgcAMQPFramePayload_Method_BasicGetOk;
  const aContent: TsgcAMQPMessageContent);
begin
  DoLog('#AMQP_basic_GetOk: ' + aChannel + ' ' + IntToStr(aGetOk.MessageCount) +
    ' ' + aContent.Body.AsString);

  txtDeliveryTag.Text := IntToStr(aGetOk.DeliveryTag);
end;

procedure TfrmClientAMQP.AMQPAMQPBasicQoS(Sender: TObject;
  const aChannel: string; const aQoS: TsgcAMQPFramePayload_Method_BasicQoS);
begin
  DoLog('#AMQP_basic_qos: ' + aChannel + ' ' + IntToStr(aQoS.PrefetchSize) + ' '
    + IntToStr(aQoS.PrefetchCount) + ' ' + BoolToStr(aQoS.Global));
end;

procedure TfrmClientAMQP.AMQPAMQPBasicRecoverOk(Sender: TObject;
  const aChannel: string);
begin
  DoLog('#AMQP_basic_RecoverOk: ' + aChannel);
end;

procedure TfrmClientAMQP.AMQPAMQPBasicReturn(Sender: TObject;
  const aChannel: string;
  const aReturn: TsgcAMQPFramePayload_Method_BasicReturn;
  const aContent: TsgcAMQPMessageContent);
begin
  DoLog('#AMQP_basic_return: ' + aChannel + ' ' + IntToStr(aReturn.ReplyCode) +
    ' ' + aReturn.ReplyText + ' ' + aContent.Body.AsString);
end;

procedure TfrmClientAMQP.AMQPAMQPChannelClose(Sender: TObject;
  const aChannel: string;
  const aChannelClose: TsgcAMQPFramePayload_Method_ChannelClose; aAck: Boolean);
begin
  DoLog('#AMQP_channel_Close: ' + aChannel + ' ' + aChannelClose.ReplyText);

  TThread.Queue(nil,
    procedure
    var
      i: Integer;
    begin
      if Assigned(listChannels) then
      begin
        for i := 0 to listChannels.GetCount - 1 do
        begin
          if listChannels.Items[i].Caption = aChannel then
            listChannels.Items[i].Selected := True;
        end;

        listChannels.DeleteSelected;
      end;
    end);
end;

procedure TfrmClientAMQP.AMQPAMQPChannelOpen(Sender: TObject;
const aChannel: string);
begin
  DoLog('#AMQP_channel_open: ' + aChannel);

  TThread.Queue(nil,
    procedure
    begin
      if Assigned(listChannels) then
        listChannels.AddItem(aChannel, nil);
    end);
end;

procedure TfrmClientAMQP.AMQPAMQPConnect(Sender: TObject);
begin
  DoLog('#AMQP_connected');
end;

procedure TfrmClientAMQP.AMQPAMQPDisconnect(Sender: TObject;
const aClose: TsgcAMQPFramePayload_Method_ConnectionClose; aAck: Boolean);
begin
  DoLog('#AMQP_disconnected: ' + IntToStr(aClose.ReplyCode) + ' ' +
    aClose.ReplyText);

  TThread.Queue(nil,
    procedure
    begin
      if Assigned(listChannels) then
        listChannels.Clear;
      if Assigned(listExchanges) then
        listExchanges.Clear;
    end);
end;

procedure TfrmClientAMQP.AMQPAMQPException(Sender: TObject; E: Exception);
begin
  DoLog('#AMQP_exception: ' + E.Message);
end;

procedure TfrmClientAMQP.AMQPAMQPExchangeDeclare(Sender: TObject;
const aChannel, aExchange: string);
begin
  DoLog('#AMQP_exchange_declare: [' + aChannel + '] ' + aExchange);

  TThread.Queue(nil,
    procedure
    begin
      Exchanges.Add(aChannel + Exchanges.NameValueSeparator + aExchange);
      DoListExchanges(aChannel);
    end);
end;

procedure TfrmClientAMQP.AMQPAMQPExchangeDelete(Sender: TObject;
const aChannel, aExchange: string);
begin
  DoLog('#AMQP_exchange_delete: [' + aChannel + '] ' + aExchange);

  TThread.Queue(nil,
    procedure
    var
      i: Integer;
    begin
      for i := 0 to Exchanges.Count - 1 do
      begin
        if Exchanges[i] = aChannel + Exchanges.NameValueSeparator + aExchange
        then
        begin
          Exchanges.Delete(i);
          break;
        end;
      end;
      DoListExchanges(aChannel);
    end);
end;

procedure TfrmClientAMQP.AMQPAMQPHeartBeat(Sender: TObject);
begin
  DoLog('#AMQP_heartbeat');
end;

procedure TfrmClientAMQP.AMQPAMQPQueueBind(Sender: TObject;
const aChannel, aQueue, aExchange: string);
begin
  DoLog('#AMQP_queue_bind: [' + aChannel + '] ' + aQueue + ' --><-- ' +
    aExchange);
end;

procedure TfrmClientAMQP.AMQPAMQPQueueDeclare(Sender: TObject;
const aChannel, aQueue: string; aMessageCount, aConsumerCount: Integer);
begin
  DoLog('#AMQP_queue_declare: [' + aChannel + '] ' + aQueue);

  TThread.Queue(nil,
    procedure
    begin
      Queues.Add(aChannel + Exchanges.NameValueSeparator + aQueue);
      DoListQueues(aChannel);
    end);
end;

procedure TfrmClientAMQP.AMQPAMQPQueueDelete(Sender: TObject;
const aChannel, aQueue: string; aMessageCount: Integer);
begin
  DoLog('#AMQP_queue_delete: [' + aChannel + '] ' + aQueue);

  TThread.Queue(nil,
    procedure
    var
      i: Integer;
    begin
      for i := 0 to Exchanges.Count - 1 do
      begin
        if Queues[i] = aChannel + Exchanges.NameValueSeparator + aQueue then
        begin
          Queues.Delete(i);
          break;
        end;
      end;
      DoListQueues(aChannel);
    end);
end;

procedure TfrmClientAMQP.AMQPAMQPQueuePurge(Sender: TObject;
const aChannel, aQueue: string; aMessageCount: Integer);
begin
  DoLog('#AMQP_queue_purge: [' + aChannel + '] ' + aQueue + ' (' +
    IntToStr(aMessageCount) + ')');
end;

procedure TfrmClientAMQP.AMQPAMQPQueueUnBind(Sender: TObject;
const aChannel, aQueue, aExchange: string);
begin
  DoLog('#AMQP_queue_unbind: [' + aChannel + '] ' + aQueue + ' <-- --> ' +
    aExchange);
end;

procedure TfrmClientAMQP.AMQPAMQPTransactionOk(Sender: TObject;
const aChannel: string; aTransaction: TsgcAMQPTransaction);
begin
  case aTransaction of
    amqpTransactionSelect:
      DoLog('#AMQP_transaction_ok: [' + aChannel + '] select');
    amqpTransactionCommit:
      DoLog('#AMQP_transaction_ok: [' + aChannel + '] commit');
    amqpTransactionRollback:
      DoLog('#AMQP_transaction_ok: [' + aChannel + '] rollback');
  end;
end;

procedure TfrmClientAMQP.btnAckMessageClick(Sender: TObject);
begin
  if ((txtChannelName.Text <> '') and (txtDeliveryTag.Text <> '')) then
    AMQP.AckMessage(txtChannelName.Text, StrToInt(txtDeliveryTag.Text),
      chkAckMultiple.checked);
end;

procedure TfrmClientAMQP.btnChannelOpenClick(Sender: TObject);
begin
  AMQP.OpenChannel(txtChannelName.Text);
end;

procedure TfrmClientAMQP.btnConsumeClick(Sender: TObject);
begin
  if (txtChannelName.Text <> '') and (txtQueueName.Text <> '') then
    AMQP.Consume(txtChannelName.Text, txtQueueName.Text,
      txtConsumeConsumerTag.Text, chkConsumeNoLocal.checked,
      chkConsumeNoAck.checked, chkConsumeExclusive.checked,
      chkConsumeNoWait.checked);
end;

procedure TfrmClientAMQP.btnExchangeDeclareClick(Sender: TObject);
begin
  if (txtChannelName.Text <> '') and (txtExchangeName.Text <> '') then
    AMQP.DeclareExchange(txtChannelName.Text, txtExchangeName.Text,
      txtExchangeType.Text, chkExchangePassive.checked,
      chkExchangeDurable.checked, chkExchangeAutoDelete.checked,
      chkExchangeInternal.checked, chkExchangeNoWait.checked);
end;

procedure TfrmClientAMQP.btnQueueBindClick(Sender: TObject);
begin
  if (txtChannelName.Text <> '') and (txtExchangeName.Text <> '') and
    (txtQueueName.Text <> '') then
    AMQP.BindQueueEx(txtChannelName.Text, txtQueueName.Text, txtExchangeName.Text,
      txtQueueRoutingKey.Text);
end;

procedure TfrmClientAMQP.btnQueueDeclareClick(Sender: TObject);
begin
  if (txtChannelName.Text <> '') and (txtQueueName.Text <> '') then
    AMQP.DeclareQueue(txtChannelName.Text, txtQueueName.Text,
      chkQueuePassive.checked, chkQueueDurable.checked,
      chkQueueExclusive.checked, chkQueueAutoDelete.checked,
      chkQueueNoWait.checked);
end;

procedure TfrmClientAMQP.btnQueueDeleteClick(Sender: TObject);
begin
  if (txtChannelName.Text <> '') and (txtQueueName.Text <> '') then
    AMQP.DeleteQueue(txtChannelName.Text, txtQueueName.Text);
end;

procedure TfrmClientAMQP.btnQueuePurgeClick(Sender: TObject);
begin
  if (txtChannelName.Text <> '') and (txtQueueName.Text <> '') then
    AMQP.PurgeQueue(txtChannelName.Text, txtQueueName.Text);
end;

procedure TfrmClientAMQP.btnQueueUnBindClick(Sender: TObject);
begin
  if (txtChannelName.Text <> '') and (txtExchangeName.Text <> '') and
    (txtQueueName.Text <> '') then
    AMQP.UnBindQueue(txtChannelName.Text, txtQueueName.Text,
      txtExchangeName.Text, txtQueueRoutingKey.Text);
end;

procedure TfrmClientAMQP.btnStartClick(Sender: TObject);
begin
  WSClient.NotifyEvents := neNoSync;
  WSClient.Specifications.RFC6455 := False;

  if chkTLS.checked then
    WSClient.Port := StrToInt(txtSSLPort.Text)
  else
    WSClient.Port := StrToInt(txtDefaultPort.Text);
  WSClient.Host := txtHost.Text;

  WSClient.TLS := chkTLS.checked;

  WSClient.Proxy.Enabled := chkProxy.checked;
  WSClient.Proxy.Username := txtProxyUsername.Text;
  WSClient.Proxy.Password := txtProxyPassword.Text;
  WSClient.Proxy.Host := txtProxyHost.Text;
  if txtProxyPort.Text <> '' then
    WSClient.Proxy.Port := StrToInt(txtProxyPort.Text);

  // ... active
  WSClient.Active := True;
  if WSClient.Active then
    pnlClientOptions.Enabled := False;
end;

procedure TfrmClientAMQP.btnStopClick(Sender: TObject);
begin
  WSClient.Active := False;

  if not WSClient.Active then
    pnlClientOptions.Enabled := True;
end;

procedure TfrmClientAMQP.btnSetQoSClick(Sender: TObject);
begin
  if (txtChannelName.Text <> '') and (txtQueueName.Text <> '') then
    AMQP.SetQoS(txtChannelName.Text, StrToInt(txtQoSPrefetchSize.Text),
      StrToInt(txtQoSPrefetchCount.Text), chkQoSGlobal.checked)
end;

procedure TfrmClientAMQP.btnCancelConsumeClick(Sender: TObject);
begin
  if txtChannelName.Text <> '' then
    AMQP.CancelConsume(txtChannelName.Text, txtConsumeConsumerTag.Text,
      chkConsumeNoWait.checked);
end;

procedure TfrmClientAMQP.btnCommitTransactionClick(Sender: TObject);
begin
  if txtChannelName.Text <> '' then
    AMQP.CommitTransaction(txtChannelName.Text);
end;

procedure TfrmClientAMQP.btnGetMessageClick(Sender: TObject);
begin
  if (txtChannelName.Text <> '') and (txtQueueName.Text <> '') then
    AMQP.GetMessage(txtChannelName.Text, txtQueueName.Text);
end;

procedure TfrmClientAMQP.btnPublishMessageClick(Sender: TObject);
begin
  if (txtChannelName.Text <> '') and (txtExchangeName.Text <> '') then
    AMQP.PublishMessage(txtChannelName.Text, txtExchangeName.Text,
      txtRoutingKey.Text, txtPublishMessage.Text, chkMandatory.checked,
      chkImmediate.checked);
end;

procedure TfrmClientAMQP.btnRecoverAsyncMessageClick(Sender: TObject);
begin
  if txtChannelName.Text <> '' then
    AMQP.RecoverAsync(txtChannelName.Text, chkRecoverRequeue.checked);
end;

procedure TfrmClientAMQP.btnRejectMessageClick(Sender: TObject);
begin
  if ((txtChannelName.Text <> '') and (txtDeliveryTag.Text <> '')) then
    AMQP.RejectMessage(txtChannelName.Text, StrToInt(txtDeliveryTag.Text),
      chkRejectRequeue.checked);
end;

procedure TfrmClientAMQP.btnRecoverMessageClick(Sender: TObject);
begin
  if txtChannelName.Text <> '' then
    if AMQP.RecoverEx(txtChannelName.Text, chkRecoverRequeue.checked) then
      ShowMessage('ok');
end;

procedure TfrmClientAMQP.btnRollbackTransactionClick(Sender: TObject);
begin
  if txtChannelName.Text <> '' then
    AMQP.RollbackTransaction(txtChannelName.Text);
end;

procedure TfrmClientAMQP.btnSelectTransactionClick(Sender: TObject);
begin
  if txtChannelName.Text <> '' then
    AMQP.SelectTransactionEx(txtChannelName.Text);
end;

procedure TfrmClientAMQP.ChannelClose1Click(Sender: TObject);
begin
  if txtChannelName.Text <> '' then
    AMQP.CloseChannel(txtChannelName.Text);
end;

procedure TfrmClientAMQP.ChannelDisable1Click(Sender: TObject);
begin
  if txtChannelName.Text <> '' then
    AMQP.DisableChannel(txtChannelName.Text);
end;

procedure TfrmClientAMQP.ChannelEnable1Click(Sender: TObject);
begin
  if txtChannelName.Text <> '' then
    AMQP.EnableChannel(txtChannelName.Text);
end;

procedure TfrmClientAMQP.DeleteExchange1Click(Sender: TObject);
begin
  if (txtChannelName.Text <> '') and (txtExchangeName.Text <> '') then
    AMQP.DeleteExchange(txtChannelName.Text, txtExchangeName.Text);
end;

procedure TfrmClientAMQP.DeleteQueue1Click(Sender: TObject);
begin
  if (txtChannelName.Text <> '') and (txtQueueName.Text <> '') then
    AMQP.DeleteQueue(txtChannelName.Text, txtQueueName.Text);
end;

procedure TfrmClientAMQP.DoListExchanges(const aChannel: string);
var
  i: Integer;
begin
  listExchanges.Clear;

  for i := 0 to Exchanges.Count - 1 do
  begin
    if Exchanges.Names[i] = aChannel then
      listExchanges.AddItem(Exchanges.ValueFromIndex[i], nil);
  end;
end;

procedure TfrmClientAMQP.DoListQueues(const aChannel: string);
var
  i: Integer;
begin
  listQueues.Clear;

  for i := 0 to Queues.Count - 1 do
  begin
    if Queues.Names[i] = aChannel then
      listQueues.AddItem(Queues.ValueFromIndex[i], nil);
  end;
end;

procedure TfrmClientAMQP.DoLog(const aText: string);
begin
  TThread.Queue(nil,
    procedure
    begin
      if Assigned(memoLog) then
        memoLog.Lines.Add(aText);
    end);
end;

function TfrmClientAMQP.GetExchanges: TStringList;
begin
  if not Assigned(FExchanges) then
    FExchanges := TStringList.Create;
  Result := FExchanges;
end;

function TfrmClientAMQP.GetQueues: TStringList;
begin
  if not Assigned(FQueues) then
    FQueues := TStringList.Create;
  Result := FQueues;
end;

procedure TfrmClientAMQP.listChannelsClick(Sender: TObject);
var
  i: Integer;
begin
  i := listChannels.ItemIndex;
  if i >= 0 then
  begin
    txtChannelName.Text := listChannels.Items[i].Caption;
    DoListExchanges(txtChannelName.Text);
    DoListQueues(txtChannelName.Text);
  end
  else
    listExchanges.Clear;
end;

procedure TfrmClientAMQP.listExchangesClick(Sender: TObject);
var
  i: Integer;
begin
  i := listExchanges.ItemIndex;
  if i >= 0 then
    txtExchangeName.Text := listExchanges.Items[i].Caption;
end;

procedure TfrmClientAMQP.listQueuesClick(Sender: TObject);
var
  i: Integer;
begin
  i := listQueues.ItemIndex;
  if i >= 0 then
    txtQueueName.Text := listQueues.Items[i].Caption;
end;

procedure TfrmClientAMQP.WSClientException(Connection: TsgcWSConnection;
E: Exception);
begin
  DoLog('#exception:' + E.Message);
end;

end.
```

