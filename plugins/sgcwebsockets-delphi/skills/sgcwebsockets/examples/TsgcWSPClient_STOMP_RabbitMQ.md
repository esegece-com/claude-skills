# TsgcWSPClient_STOMP_RabbitMQ - Example

Full source of `uWebSocketClient.pas` from the **01.WebSocket_Quick_Start/02.WebSocket_Clients_APIs** demo, which uses `TsgcWSPClient_STOMP_RabbitMQ`.

API reference: [TsgcWSPClient_STOMP_RabbitMQ](../reference/api/TsgcWSPClient_STOMP_RabbitMQ.md)
Source demo: `01.WebSocket_Quick_Start/02.WebSocket_Clients_APIs` (file `uWebSocketClient.pas`)

```pascal
unit uWebSocketClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls,
  // sgc
  sgcWebSocket_Classes, sgcWebSocket_Client, sgcWebSocket, StdCtrls,
  sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_Protocol_MQTT_Client, sgcWebSocket_Protocol_MQTT_Message,
  sgcWebSocket_Protocol_STOMP_RabbitMQ_Client,
  sgcWebSocket_Protocol_STOMP_Broker_Client, sgcWebSocket_Protocol_STOMP_Client,
  sgcWebSocket_API_SignalR, sgcWebSocket_APIs,
  sgcWebSocket_API_SocketIO, sgcWebSocket_API_Pusher,
  sgcWebSocket_API_SignalRCore, sgcBase_Classes,
  sgcTCP_Classes, sgcWebSocket_API_Discord,
  sgcHTTP_API_Coinbase, sgcHTTP_API_Kraken, sgcHTTP,
  sgcSocket_Classes;

type
  TfrmWebSocketClient = class(TForm)
    pnlClient: TPanel;
    memoLog: TMemo;
    WSClient: TsgcWebSocketClient;
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
    txtPort: TEdit;
    chkProxy: TCheckBox;
    Label7: TLabel;
    txtProxyUsername: TEdit;
    txtProxyPassword: TEdit;
    Label8: TLabel;
    Label9: TLabel;
    txtProxyHost: TEdit;
    txtProxyPort: TEdit;
    Label10: TLabel;
    pnlTop: TPanel;
    PageControl1: TPageControl;
    tabWebSocket: TTabSheet;
    tabMQTT: TTabSheet;
    btnSubscribeMQTT: TButton;
    btnUnsubscribeMQTT: TButton;
    txtChannelMQTT: TEdit;
    Label1: TLabel;
    btnPublishMQTT: TButton;
    txtPublishChannelMQTT: TEdit;
    txtPublishMessageMQTT: TEdit;
    cboQoSMQTT: TComboBox;
    chkRetainMQTT: TCheckBox;
    Label12: TLabel;
    Label2: TLabel;
    btnPingMQTT: TButton;
    pnlMemo: TPanel;
    cboServerMQTT: TComboBox;
    Label15: TLabel;
    MQTT: TsgcWSPClient_MQTT;
    Label11: TLabel;
    cboServerWebSocket: TComboBox;
    Label13: TLabel;
    txtMessage: TEdit;
    btnSend: TButton;
    Label14: TLabel;
    txtParameters: TEdit;
    chkOverWebSocket: TCheckBox;
    tabSTOMP: TTabSheet;
    Label6: TLabel;
    cboServerSTOMP: TComboBox;
    btnSubscribeSTOMP: TButton;
    btnUnSubscribeSTOMP: TButton;
    txtChannelSTOMP: TEdit;
    Label16: TLabel;
    btnPublishSTOMP: TButton;
    txtPublishChannelSTOMP: TEdit;
    txtPublishMessageSTOMP: TEdit;
    Label17: TLabel;
    btnPingSTOMP: TButton;
    Label18: TLabel;
    STOMP: TsgcWSPClient_STOMP_RabbitMQ;
    tabSIGNALR: TTabSheet;
    SIGNALR: TsgcWSAPI_SignalR;
    txtSignalRUser: TEdit;
    btnSignalRNewUser: TButton;
    btnSignalRSendMessage: TButton;
    txtSignalRMessage: TEdit;
    btnSignalROpenBrowser: TButton;
    SOCKETIO: TsgcWSAPI_SocketIO;
    tabSOCKETIO: TTabSheet;
    txtSocketIOUserName: TEdit;
    btnSocketIONewUser: TButton;
    txtSocketIOMessage: TEdit;
    btnSocketIOMessage: TButton;
    PUSHER: TsgcWSAPI_Pusher;
    tabPUSHER: TTabSheet;
    txtClusterPUSHER: TEdit;
    Label24: TLabel;
    txtKeyPUSHER: TEdit;
    Label25: TLabel;
    txtNamePUSHER: TEdit;
    txtVersionPUSHER: TEdit;
    txtSecretPUSHER: TEdit;
    Label26: TLabel;
    Label27: TLabel;
    chkTLSPUSHER: TCheckBox;
    Label28: TLabel;
    Label29: TLabel;
    SIGNALRCORE: TsgcWSAPI_SignalRCore;
    tabSIGNALRCORE: TTabSheet;
    btnSignalRCoreClose: TButton;
    btnSignalRCoreSendMessage: TButton;
    btnSignalRCoreOpenBrowser: TButton;
    txtSignalRCoreUser: TEdit;
    txtSignalRCoreMessage: TEdit;
    btnSignalRCoreStartStreaming: TButton;
    tabAWSAppSync: TTabSheet;
    txtAWSAppSyncAPIURL: TEdit;
    Label39: TLabel;
    txtAWSAppSyncAPIKEY: TEdit;
    Label40: TLabel;
    txtAWSAppSyncSubscription: TEdit;
    Label41: TLabel;
    cboSignalRCoreServer: TComboBox;
    Label42: TLabel;
    tabDiscord: TTabSheet;
    DISCORD: TsgcWSAPI_Discord;
    txtDiscordBotName: TEdit;
    txtDiscordBotURL: TEdit;
    txtDiscordBotToken: TEdit;
    Label45: TLabel;
    Label46: TLabel;
    Label47: TLabel;
    btnDiscordGetUser: TButton;
    txtAppIdPUSHER: TEdit;
    Label84: TLabel;
    PageControl6: TPageControl;
    tabPusherWebsocket: TTabSheet;
    tabPusherREST: TTabSheet;
    btnSubscribePUSHER: TButton;
    btnUnSubscribePUSHER: TButton;
    txtChannelPUSHER: TEdit;
    btnPublishPUSHER: TButton;
    cboPUSHERChannelTypes: TComboBox;
    Label91: TLabel;
    Label92: TLabel;
    Label93: TLabel;
    txtEventPUSHER: TEdit;
    txtPublishPUSHER: TEdit;
    Label94: TLabel;
    txtPUSHERChannelREST: TEdit;
    Label95: TLabel;
    txtPUSHEREventREST: TEdit;
    btnPUSHERTriggerEvent: TButton;
    txtPUSHERDataREST: TEdit;
    btnPUSHERGetChannels: TButton;
    btnPUSHERGetUsers: TButton;
    btnPUSHERBatchEvents: TButton;
    btnPUSHERTerminateUser: TButton;
    txtPUSHERBatchREST: TEdit;
    txtPUSHERUserIdREST: TEdit;
    btnSocketIOOpenBrowser: TButton;
    procedure btnSubscribeMQTTClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure btnUnsubscribeMQTTClick(Sender: TObject);
    procedure btnPublishMQTTClick(Sender: TObject);
    procedure btnSendClick(Sender: TObject);
    procedure btnSubscribeSTOMPClick(Sender: TObject);
    procedure btnUnSubscribeSTOMPClick(Sender: TObject);
    procedure cboServerWebSocketChange(Sender: TObject);
    procedure cboServerMQTTChange(Sender: TObject);
    procedure MQTTMQTTPing(Connection: TsgcWSConnection);
    procedure STOMPRabbitMQConnected(Connection: TsgcWSConnection;
      Headers: TsgcWSRabbitMQSTOMPHeadersConnected);
    procedure STOMPRabbitMQDisconnected(Connection: TsgcWSConnection;
      Code: Integer);
    procedure STOMPRabbitMQError(Connection: TsgcWSConnection;
      MessageText: string; Headers: TsgcWSRabbitMQSTOMPHeadersError);
    procedure STOMPRabbitMQMessage(Connection: TsgcWSConnection;
      MessageText: string; Headers: TsgcWSRabbitMQSTOMPHeadersMessage;
      Subscription: TsgcWSBrokerSTOMPSubscriptionItem);
    procedure tabMQTTShow(Sender: TObject);
    procedure tabSTOMPShow(Sender: TObject);
    procedure tabWebSocketShow(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnPublishPUSHERClick(Sender: TObject);
    procedure btnSignalRNewUserClick(Sender: TObject);
    procedure btnSignalROpenBrowserClick(Sender: TObject);
    procedure btnSignalRSendMessageClick(Sender: TObject);
    procedure SIGNALRSignalRConnect(Sender: TObject; MessageId, aData: string);
    procedure SIGNALRSignalRDisconnect(Sender: TObject; aCloseCode: Integer);
    procedure SIGNALRSignalRError(Sender: TObject; Error: string);
    procedure SIGNALRSignalRKeepAlive(Sender: TObject);
    procedure SIGNALRSignalRMessage(Sender: TObject; MessageId, aData: string);
    procedure SIGNALRSignalRResult(Sender: TObject;
      InvocationId, Result, Error: string);
    procedure tabSIGNALRShow(Sender: TObject);
    procedure tabSOCKETIOShow(Sender: TObject);
    procedure btnSocketIONewUserClick(Sender: TObject);
    procedure btnSocketIOMessageClick(Sender: TObject);
    procedure btnSubscribePUSHERClick(Sender: TObject);
    procedure btnUnSubscribePUSHERClick(Sender: TObject);
    procedure btnDiscordGetUserClick(Sender: TObject);
    procedure btnSignalRCoreCloseClick(Sender: TObject);
    procedure btnSignalRCoreSendMessageClick(Sender: TObject);
    procedure btnSignalRCoreOpenBrowserClick(Sender: TObject);
    procedure btnSignalRCoreStartStreamingClick(Sender: TObject);
    procedure btnPingMQTTClick(Sender: TObject);
    procedure btnPublishSTOMPClick(Sender: TObject);
    procedure btnPUSHERGetChannelsClick(Sender: TObject);
    procedure btnPUSHERGetUsersClick(Sender: TObject);
    procedure btnPUSHERTriggerEventClick(Sender: TObject);
    procedure btnPUSHERBatchEventsClick(Sender: TObject);
    procedure btnPUSHERTerminateUserClick(Sender: TObject);
    procedure btnSocketIOOpenBrowserClick(Sender: TObject);
    procedure cboServerSTOMPChange(Sender: TObject);
    procedure cboSignalRCoreServerChange(Sender: TObject);
    procedure DISCORDConnect(Connection: TsgcWSConnection);
    procedure DISCORDDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure DISCORDDiscordDispatch(Sender: TObject;
      const aEvent, RawData: string);
    procedure DISCORDDiscordReady(Sender: TObject; const RawData: string);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure KRAKEN_FUTURESKrakenFuturesConnect(Sender: TObject;
      Version: string);
    procedure KRAKEN_FUTURESKrakenFuturesError(Sender: TObject; Error: string);
    procedure KRAKEN_FUTURESKrakenFuturesSubscribed(Sender: TObject;
      Feed, ProductId: string);
    procedure KRAKEN_FUTURESKrakenFuturesUnSubscribed(Sender: TObject;
      Feed, ProductId: string);
    procedure KRAKEN_FUTURESKrakenHTTPException(Sender: TObject; E: Exception);
    procedure MQTTMQTTBeforeConnect(Connection: TsgcWSConnection;
      var aCleanSession: Boolean; var aClientIdentifier: string);
    procedure MQTTMQTTConnect(Connection: TsgcWSConnection;
      const Session: Boolean; const ReasonCode: Integer;
      const ReasonName: string;
      const ConnectProperties: TsgcWSMQTTCONNACKProperties);
    procedure MQTTMQTTDisconnect(Connection: TsgcWSConnection;
      ReasonCode: Integer; const ReasonName: string;
      DisconnectProperties: TsgcWSMQTTDISCONNECTProperties);
    procedure MQTTMQTTPubAck(Connection: TsgcWSConnection;
      aPacketIdentifier: Word; ReasonCode: Integer; const ReasonName: string;
      PubAckProperties: TsgcWSMQTTPUBACKProperties);
    procedure MQTTMQTTPubComp(Connection: TsgcWSConnection;
      aPacketIdentifier: Word; ReasonCode: Integer; const ReasonName: string;
      PubCompProperties: TsgcWSMQTTPUBCOMPProperties);
    procedure MQTTMQTTPublish(Connection: TsgcWSConnection;
      aTopic, aText: string; PublishProperties: TsgcWSMQTTPublishProperties);
    procedure MQTTMQTTPubRec(Connection: TsgcWSConnection;
      aPacketIdentifier: Word; ReasonCode: Integer; const ReasonName: string;
      PubRecProperties: TsgcWSMQTTPUBRECProperties);
    procedure MQTTMQTTSubscribe(Connection: TsgcWSConnection;
      aPacketIdentifier: Word; aCodes: TsgcWSSUBACKS;
      SubscribeProperties: TsgcWSMQTTSUBACKProperties);
    procedure MQTTMQTTUnSubscribe(Connection: TsgcWSConnection;
      aPacketIdentifier: Word; aCodes: TsgcWSUNSUBACKS;
      UnsubscribeProperties: TsgcWSMQTTUNSUBACKProperties);
    procedure PUSHERDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure PUSHERPusherConnect(Sender: TObject; Socket_id: string;
      Timeout: Integer);
    procedure PUSHERPusherError(Sender: TObject; Code: Integer; Msg: string);
    procedure PUSHERPusherEvent(Sender: TObject; Event, Channel, Data: string);
    procedure PUSHERPusherSubscribe(Sender: TObject; Channel, Data: string);
    procedure PUSHERPusherMemberAdded(Sender: TObject;
      Channel, UserId, UserInfo: string);
    procedure PUSHERPusherMemberRemoved(Sender: TObject;
      Channel, UserId, UserInfo: string);
    procedure PUSHERPusherSubscriptionCount(Sender: TObject;
      Channel: string; SubscriptionCount: Integer);
    procedure PUSHERPusherCacheMiss(Sender: TObject; Channel: string);
    procedure SIGNALRCORESignalRCoreCancelInvocation(Sender: TObject;
      CancelInvocation: TSignalRCore_CancelInvocation);
    procedure SIGNALRCORESignalRCoreClose(Sender: TObject;
      Close: TSignalRCore_Close);
    procedure SIGNALRCORESignalRCoreCompletion(Sender: TObject;
      Completion: TSignalRCore_Completion);
    procedure SIGNALRCORESignalRCoreConnect(Sender: TObject;
      Connect: TSignalRCore_Connect);
    procedure SIGNALRCORESignalRCoreDisconnect(Sender: TObject;
      CloseCode: Integer; CloseReason: string);
    procedure SIGNALRCORESignalRCoreError(Sender: TObject;
      Error: TSignalRCore_Error);
    procedure SIGNALRCORESignalRCoreInvocation(Sender: TObject;
      Invocation: TSignalRCore_Invocation);
    procedure SIGNALRCORESignalRCoreKeepAlive(Sender: TObject);
    procedure SIGNALRCORESignalRCoreStreamInvocation(Sender: TObject;
      StreamInvocation: TSignalRCore_Invocation);
    procedure SIGNALRCORESignalRCoreStreamItem(Sender: TObject;
      StreamItem: TSignalRCore_StreamItem; var Cancel: Boolean);
    procedure tabAWSAppSyncShow(Sender: TObject);
    procedure tabDiscordShow(Sender: TObject);
    procedure tabPUSHERShow(Sender: TObject);
    procedure tabSIGNALRCOREShow(Sender: TObject);
    procedure txtDiscordBotTokenChange(Sender: TObject);
  private
    FMQTTClientId: string;
    FMQTTSubscribeTopic: string;
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
    procedure DoBeforeConnectAWSAppSync;
  private
    procedure DoServerMQTT(aItemIndex: Integer);
    procedure DoServerWebSocket(aItemIndex: Integer);
    procedure DoServerSTOMP(aItemIndex: Integer);
    procedure DoServerSIGNALR;
    procedure DoServerSOCKETIO;
    procedure DoServerPUSHER;
    procedure DoServerSIGNALRCORE(aItemIndex: Integer);
    procedure DoServerAWSAppSync;
    procedure DoServerDISCORD;
  end;

var
  frmWebSocketClient: TfrmWebSocketClient;

implementation

uses
  sgcWebSocket_Helpers, sgcJSON, StrUtils, sgcBase_Helpers,
  ShellAPI, DateUtils;
{$R *.dfm}

procedure TfrmWebSocketClient.btnSubscribeMQTTClick(Sender: TObject);
begin
  MQTT.Subscribe(txtChannelMQTT.Text);
end;

procedure TfrmWebSocketClient.btnStartClick(Sender: TObject);
begin
  WSClient.Host := txtHost.Text;
  WSClient.Port := StrToInt(txtPort.Text);
  WSClient.Options.Parameters := txtParameters.Text;
  WSClient.TLS := chkTLS.Checked;

  WSClient.Specifications.RFC6455 := chkOverWebSocket.Checked;

  WSClient.Proxy.Enabled := chkProxy.Checked;
  WSClient.Proxy.Username := txtProxyUsername.Text;
  WSClient.Proxy.Password := txtProxyPassword.Text;
  WSClient.Proxy.Host := txtProxyHost.Text;
  if txtProxyPort.Text <> '' then
    WSClient.Proxy.Port := StrToInt(txtProxyPort.Text);

  WSClient.Extensions.PerMessage_Deflate.Enabled := chkCompressed.Checked;

  // ... active
  DoBeforeConnect;
  WSClient.Active := True;
  if WSClient.Active then
    pnlClientOptions.Enabled := False;
end;

procedure TfrmWebSocketClient.btnStopClick(Sender: TObject);
begin
  WSClient.Active := False;

  if not WSClient.Active then
    pnlClientOptions.Enabled := True;
end;

procedure TfrmWebSocketClient.btnUnsubscribeMQTTClick(Sender: TObject);
begin
  MQTT.Unsubscribe(txtChannelMQTT.Text);
end;

procedure TfrmWebSocketClient.btnPublishMQTTClick(Sender: TObject);
begin
  MQTT.Publish(txtPublishChannelMQTT.Text, txtPublishMessageMQTT.Text,
    TmqttQoS(cboQoSMQTT.itemIndex), chkRetainMQTT.Checked);
end;

procedure TfrmWebSocketClient.btnSendClick(Sender: TObject);
begin
  if WSClient.Active then
  begin
    if txtMessage.Text = '' then
      raise Exception.Create('Type a Message before send a message');

    WSClient.WriteData(txtMessage.Text);

    txtMessage.Text := '';
  end
  else
    raise Exception.Create('Not connected');
end;

procedure TfrmWebSocketClient.btnSubscribeSTOMPClick(Sender: TObject);
begin
  STOMP.SubscribeTopic(txtChannelSTOMP.Text);
end;

procedure TfrmWebSocketClient.btnUnSubscribeSTOMPClick(Sender: TObject);
begin
  STOMP.UnSubscribeTopic(txtChannelSTOMP.Text);
end;

procedure TfrmWebSocketClient.btnPublishPUSHERClick(Sender: TObject);
begin
  case cboPusherChannelTypes.ItemIndex of
    0: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscPublicChannel, txtPublishPUSHER.Text);
    1: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscPrivateChannel, txtPublishPUSHER.Text);
    2: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscPresenceChannel, txtPublishPUSHER.Text);
    3: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscCacheChannel, txtPublishPUSHER.Text);
    4: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscPrivateCacheChannel, txtPublishPUSHER.Text);
    5: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscPresenceCacheChannel, txtPublishPUSHER.Text);
    6: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscPrivateEncryptedChannel, txtPublishPUSHER.Text);
    7: PUSHER.Publish(txtEventPUSHER.Text, txtChannelPUSHER.Text, pscPrivateEncryptedCacheChannel, txtPublishPUSHER.Text);
  end;
end;

procedure TfrmWebSocketClient.btnSocketIOMessageClick(Sender: TObject);
begin
  WSClient.WriteData(Format('5:::{"name":"sendchat","args":["%s"]}', [txtSocketIOMessage.Text]));
end;

procedure TfrmWebSocketClient.btnSocketIONewUserClick(Sender: TObject);
begin
  WSClient.WriteData(Format('5:::{"name":"adduser","args":["%s"]}', [txtSocketIOUserName.Text]));
end;

procedure TfrmWebSocketClient.btnSignalRNewUserClick(Sender: TObject);
begin
  SIGNALR.WriteData('{"H":"chathub","M":"Connect","A":["' + txtSignalRUser.Text
    + '"],"I":0}');
end;

procedure TfrmWebSocketClient.btnSignalROpenBrowserClick(Sender: TObject);
begin
{$IFDEF UNICODE}
  ShellExecute(Application.Handle, 'open', PWideChar('chrome'),
    PWideChar('http://www.sgcwebsockets.com:81'), '', 0);
{$ELSE}
  ShellExecute(Application.Handle, 'open', PAnsiChar('chrome'),
    PAnsiChar('http://www.sgcwebsockets.com:81'), '', 0);
{$ENDIF}
end;

procedure TfrmWebSocketClient.btnSignalRSendMessageClick(Sender: TObject);
begin
  SIGNALR.WriteData('{"H":"chathub","M":"Send","A":["' + txtSignalRMessage.Text
    + '"],"I":' + FormatDateTime('nnsszz', Now) + '}');
end;

procedure TfrmWebSocketClient.btnSubscribePUSHERClick(Sender: TObject);
begin
  case cboPusherChannelTypes.ItemIndex of
    0: PUSHER.Subscribe(txtChannelPUSHER.Text, pscPublicChannel);
    1: PUSHER.Subscribe(txtChannelPUSHER.Text, pscPrivateChannel);
    2: PUSHER.Subscribe(txtChannelPUSHER.Text, pscPresenceChannel, '{"user_id": "1234", "user_info": {"name": "Phil Leggetter"}}');
    3: PUSHER.Subscribe(txtChannelPUSHER.Text, pscCacheChannel);
    4: PUSHER.Subscribe(txtChannelPUSHER.Text, pscPrivateCacheChannel);
    5: PUSHER.Subscribe(txtChannelPUSHER.Text, pscPresenceCacheChannel, '{"user_id": "1234", "user_info": {"name": "Phil Leggetter"}}');
    6: PUSHER.Subscribe(txtChannelPUSHER.Text, pscPrivateEncryptedChannel);
    7: PUSHER.Subscribe(txtChannelPUSHER.Text, pscPrivateEncryptedCacheChannel);
  end;
end;

procedure TfrmWebSocketClient.btnUnSubscribePUSHERClick(Sender: TObject);
begin
  case cboPusherChannelTypes.ItemIndex of
    0: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscPublicChannel);
    1: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscPrivateChannel);
    2: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscPresenceChannel);
    3: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscCacheChannel);
    4: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscPrivateCacheChannel);
    5: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscPresenceCacheChannel);
    6: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscPrivateEncryptedChannel);
    7: PUSHER.UnSubscribe(txtChannelPUSHER.Text, pscPrivateEncryptedCacheChannel);
  end;
end;

procedure TfrmWebSocketClient.btnDiscordGetUserClick(Sender: TObject);
begin
  DoLog('#Discord GET: ' + DISCORD.GET_Request('/users/@me'));
end;

procedure TfrmWebSocketClient.btnSignalRCoreCloseClick(Sender: TObject);
begin
  SIGNALRCORE.Close;
end;

procedure TfrmWebSocketClient.btnSignalRCoreSendMessageClick(Sender: TObject);
begin
  case cboSignalRCoreServer.itemIndex of
    0:
      SIGNALRCORE.Invoke('SendMessage', [txtSignalRCoreUser.Text,
        txtSignalRCoreMessage.Text]);
    1:
      SIGNALRCORE.Invoke('Send', [txtSignalRCoreMessage.Text]);
  end;
end;

procedure TfrmWebSocketClient.btnSignalRCoreOpenBrowserClick(Sender: TObject);
begin
{$IFDEF UNICODE}
  ShellExecute(Application.Handle, 'open', PWideChar('chrome'),
    PWideChar('http://www.sgcwebsockets.com:' + txtPort.Text + ''), '', 0);
{$ELSE}
  ShellExecute(Application.Handle, 'open', PAnsiChar('chrome'),
    PAnsiChar('http://www.sgcwebsockets.com:' + txtPort.Text + ''), '', 0);
{$ENDIF}
end;

procedure TfrmWebSocketClient.btnSignalRCoreStartStreamingClick
  (Sender: TObject);
var
  oCompletion: TSignalRCore_Completion;
begin
  if SIGNALRCORE.InvokeStreamAndWait('Counter', [10, 500], '1', oCompletion)
  then
    DoLog('#invoke stream ok: ' + oCompletion.Result)
  else
    DoLog('#invocke stream error: ' + oCompletion.Error);
end;

procedure TfrmWebSocketClient.btnPingMQTTClick(Sender: TObject);
begin
  MQTT.Ping;
end;

procedure TfrmWebSocketClient.btnPublishSTOMPClick(Sender: TObject);
begin
  STOMP.PublishTopic(txtPublishChannelSTOMP.Text, txtPublishMessageSTOMP.Text);
end;

procedure TfrmWebSocketClient.btnPUSHERGetChannelsClick(Sender: TObject);
begin
  DoLog(PUSHER.GetChannels);
end;

procedure TfrmWebSocketClient.btnPUSHERGetUsersClick(Sender: TObject);
begin
  DoLog(PUSHER.GetUsers(txtPUSHERChannelREST.Text));
end;

procedure TfrmWebSocketClient.btnPUSHERTriggerEventClick(Sender: TObject);
begin
  DoLog(PUSHER.TriggerEvent(txtPUSHEREventREST.Text, txtPUSHERChannelREST.Text, txtPUSHERDataREST.Text));
end;

procedure TfrmWebSocketClient.btnSocketIOOpenBrowserClick(Sender: TObject);
begin
{$IFDEF UNICODE}
  ShellExecute(Application.Handle, 'open', PWideChar('chrome'),
    PWideChar('http://www.sgcwebsockets.com:3000'), '', 0);
{$ELSE}
  ShellExecute(Application.Handle, 'open', PAnsiChar('chrome'),
    PAnsiChar('http://www.sgcwebsockets.com:3000'), '', 0);
{$ENDIF}
end;

procedure TfrmWebSocketClient.cboServerWebSocketChange(Sender: TObject);
begin
  DoServerWebSocket(cboServerWebSocket.itemIndex);
end;

procedure TfrmWebSocketClient.cboServerMQTTChange(Sender: TObject);
begin
  DoServerMQTT(cboServerMQTT.itemIndex);
end;

procedure TfrmWebSocketClient.cboServerSTOMPChange(Sender: TObject);
begin
  DoServerSTOMP(cboServerSTOMP.itemIndex);
end;

procedure TfrmWebSocketClient.cboSignalRCoreServerChange(Sender: TObject);
begin
  DoServerSIGNALRCORE(cboSignalRCoreServer.itemIndex);
end;

procedure TfrmWebSocketClient.DISCORDConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;

procedure TfrmWebSocketClient.DISCORDDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;

procedure TfrmWebSocketClient.DISCORDDiscordDispatch(Sender: TObject;
  const aEvent, RawData: string);
begin
  DoLog('#discord dispatch: ' + aEvent + ' ' + RawData);
end;

procedure TfrmWebSocketClient.DISCORDDiscordReady(Sender: TObject;
  const RawData: string);
begin
  DoLog('#discord Ready');
end;

procedure TfrmWebSocketClient.DoBeforeConnect;
begin
  if PageControl1.ActivePage = tabAWSAppSync then
    DoBeforeConnectAWSAppSync;
end;

procedure TfrmWebSocketClient.DoBeforeConnectAWSAppSync;
var
  oHTTP: TsgcHTTP1Client;
  oRequest, oResponse: TsgcStringStream;
  oJSON: TsgcJSON;
  vClientId: string;
  vTopic: string;
  vURL: string;
begin
  oHTTP := TsgcHTTP1Client.Create(nil);
  Try
    oHTTP.Request.CustomHeaders.Add('Content-Type: application/json');
    oHTTP.Request.CustomHeaders.Add('X-Api-Key: ' + txtAWSAppSyncAPIKEY.Text);
    oResponse := TsgcStringStream.Create(nil);
    Try
      oRequest := TsgcStringStream.Create('{"query": "subscription {\n  ' +
        txtAWSAppSyncSubscription.Text +
        ' {\n    id    \n    title\n    body\n  }\n}\n"}');
      Try
        oHTTP.Post(txtAWSAppSyncAPIURL.Text, oRequest, oResponse);
      Finally
        FreeAndNil(oRequest);
      End;
      oJSON := TsgcJSON.Create(nil);
      Try
        oJSON.Read(oResponse.DataString);
        vClientId := oJSON.Node['extensions'].Node['subscription'].Node
          ['mqttConnections'].Item[0].Node['client'].Value;
        vURL := oJSON.Node['extensions'].Node['subscription'].Node
          ['mqttConnections'].Item[0].Node['url'].Value;
        vTopic := oJSON.Node['extensions'].Node['subscription'].Node
          ['mqttConnections'].Item[0].Node['topics'].Item[0].Value;

        WSClient.URL := vURL;
        txtHost.Text := WSClient.Host;
        txtPort.Text := IntToStr(WSClient.Port);
        chkTLS.Checked := WSClient.TLS;
        chkOverWebSocket.Checked := True;
        txtParameters.Text := WSClient.Options.Parameters;

        FMQTTClientId := vClientId;
        FMQTTSubscribeTopic := vTopic;
      Finally
        FreeAndNil(oJSON);
      End;
    Finally
      FreeAndNil(oResponse);
    End;
  Finally
    FreeAndNil(oHTTP);
  End;
end;

procedure TfrmWebSocketClient.DoClear;
begin
  MQTT.Client := nil;
  STOMP.Client := nil;
  SOCKETIO.Client := nil;
  PUSHER.Client := nil;
  SIGNALRCORE.Client := nil;
  DISCORD.Client := nil;
end;

procedure TfrmWebSocketClient.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
end;

procedure TfrmWebSocketClient.DoServerAWSAppSync;
begin
  DoClear;
  MQTT.Client := WSClient;

  txtParameters.Text := '/';
  chkTLS.Checked := False;
  MQTT.Authentication.Enabled := False;
  MQTT.Authentication.Username := '';
  MQTT.Authentication.Password := '';
end;

procedure TfrmWebSocketClient.DoServerPUSHER;
begin
  DoClear;
  PUSHER.Pusher.AppId := txtAppIdPUSHER.Text;
  PUSHER.Pusher.Cluster := txtClusterPUSHER.Text;
  // cluster where is located your pusher account
  PUSHER.Pusher.Key := txtKeyPUSHER.Text; // your pusher api key
  PUSHER.Pusher.Name := txtNamePUSHER.Text;
  // optional, name of your application
  PUSHER.Pusher.Version := txtVersionPUSHER.Text;
  // optional, version of your application
  PUSHER.Pusher.TLS := chkTLSPUSHER.Checked; // if encrypted, set to True
  PUSHER.Pusher.Secret := txtSecretPUSHER.Text;
  // pusher secret string (needed for private and absence channels)
  PUSHER.Client := WSClient;

  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
  chkTLS.Checked := WSClient.TLS;
  chkOverWebSocket.Checked := True;
end;

procedure TfrmWebSocketClient.DoServerDISCORD;
begin
  DoClear;
  DISCORD.DiscordOptions.BotOptions.BotName := txtDiscordBotName.Text;
  DISCORD.DiscordOptions.BotOptions.BotURL := txtDiscordBotURL.Text;
  DISCORD.DiscordOptions.BotOptions.Token := txtDiscordBotToken.Text;
  DISCORD.Client := WSClient;

  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
  chkTLS.Checked := WSClient.TLS;
  chkOverWebSocket.Checked := True;
end;

procedure TfrmWebSocketClient.DoServerMQTT(aItemIndex: Integer);
begin
  DoClear;
  MQTT.Client := WSClient;

  txtParameters.Text := '/';
  chkTLS.Checked := False;
  MQTT.Authentication.Enabled := False;
  MQTT.Authentication.Username := '';
  MQTT.Authentication.Password := '';
  MQTT.MQTTVersion := mqtt311;

  case aItemIndex of
    0: // esegece.com
      begin
        txtHost.Text := 'www.sgcwebsockets.com';
        txtPort.Text := '15675';
        txtParameters.Text := '/ws';
        MQTT.Authentication.Enabled := True;
        MQTT.Authentication.Username := 'sgc';
        MQTT.Authentication.Password := 'sgc';
      end;
    1: // test.mosquitto.org
      begin
        txtHost.Text := 'test.mosquitto.org';
        txtPort.Text := '1883';
        chkTLS.Checked := False;
        chkOverWebSocket.Checked := False;
      end;
    2: // mqtt.fluux.io
      begin
        txtHost.Text := 'mqtt.fluux.io';
        txtPort.Text := '1883';
        chkTLS.Checked := False;
        chkOverWebSocket.Checked := False;
        MQTT.MQTTVersion := mqtt5;
      end;
    3: // broker.hivemq.com
      begin
        txtHost.Text := 'broker.mqttdashboard.com';
        txtPort.Text := '8000';
        txtParameters.Text := '/mqtt';
        chkTLS.Checked := False;
        chkOverWebSocket.Checked := True;
        MQTT.MQTTVersion := mqtt5;
      end;
  end;
end;

procedure TfrmWebSocketClient.DoServerSIGNALR;
begin
  DoClear;
  SIGNALR.Client := WSClient;
  SIGNALR.SIGNALR.Hubs.Clear;
  SIGNALR.SIGNALR.Hubs.Add('chathub');
  WSClient.Specifications.RFC6455 := True;

  txtHost.Text := 'www.sgcwebsockets.com';
  txtPort.Text := '81';
  chkTLS.Checked := False;
  chkOverWebSocket.Checked := WSClient.Specifications.RFC6455;
end;

procedure TfrmWebSocketClient.DoServerSIGNALRCORE(aItemIndex: Integer);
begin
  DoClear;
  SIGNALRCORE.Client := WSClient;
  case aItemIndex of
    0:
      begin
        SIGNALRCORE.SIGNALRCORE.Authentication.Enabled := False;
        SIGNALRCORE.SIGNALRCORE.Hub := '/Chathub';
        WSClient.Specifications.RFC6455 := True;

        txtHost.Text := 'www.esegece.com';
        txtPort.Text := '5000';
      end;
    1:
      begin
        SIGNALRCORE.SIGNALRCORE.Authentication.Enabled := True;
        SIGNALRCORE.SIGNALRCORE.Authentication.Authentication :=
          srcaRequestToken;
        SIGNALRCORE.SIGNALRCORE.Authentication.Username := 'mail@mail.com';
        SIGNALRCORE.SIGNALRCORE.Authentication.Password := 'secret';
        SIGNALRCORE.SIGNALRCORE.Authentication.RequestToken.PostFieldUsername
          := 'email';
        SIGNALRCORE.SIGNALRCORE.Authentication.RequestToken.PostFieldPassword :=
          'password';
        SIGNALRCORE.SIGNALRCORE.Authentication.RequestToken.PostFieldToken
          := 'token';
        SIGNALRCORE.SIGNALRCORE.Authentication.RequestToken.QueryFieldToken :=
          'access_token';
        SIGNALRCORE.SIGNALRCORE.Authentication.RequestToken.URL :=
          '/account/token';

        SIGNALRCORE.SIGNALRCORE.Hub := '/hubs/chat';
        WSClient.Specifications.RFC6455 := True;

        txtHost.Text := 'www.esegece.com';
        txtPort.Text := '5001';
      end;
  end;

  chkTLS.Checked := False;
  chkOverWebSocket.Checked := WSClient.Specifications.RFC6455;
end;

procedure TfrmWebSocketClient.DoServerSOCKETIO;
begin
  DoClear;
  SOCKETIO.SocketIO.API := ioAPI0;
  SOCKETIO.Client := WSClient;

  txtHost.Text := 'www.sgcwebsockets.com';
  txtPort.Text := '3000';
  txtParameters.Text := '/';
  chkTLS.Checked := False;
  chkOverWebSocket.Checked := True;
end;

procedure TfrmWebSocketClient.DoServerSTOMP(aItemIndex: Integer);
begin
  DoClear;
  STOMP.Client := WSClient;

  txtParameters.Text := '/';
  chkTLS.Checked := False;
  STOMP.Authentication.Enabled := False;
  STOMP.Authentication.Username := '';
  STOMP.Authentication.Password := '';

  case aItemIndex of
    0: // esegece.com
      begin
        txtHost.Text := 'www.sgcwebsockets.com';
        txtPort.Text := '15674';
        STOMP.Authentication.Enabled := True;
        STOMP.Authentication.Username := 'sgc';
        STOMP.Authentication.Password := 'sgc';
        txtParameters.Text := '/ws';
      end;
  end;
end;

procedure TfrmWebSocketClient.DoServerWebSocket(aItemIndex: Integer);
begin
  DoClear;

  chkTLS.Checked := False;
  txtParameters.Text := '';

  case aItemIndex of
    0:
      begin
        txtHost.Text := 'www.esegece.com';
        txtPort.Text := IntToStr(2052);
      end;
    1:
      begin
        txtHost.Text := 'www.esegece.com';
        txtPort.Text := IntToStr(2053);
        chkTLS.Checked := True;
      end;
  end;
end;

procedure TfrmWebSocketClient.FormClose(Sender: TObject;
  var Action: TCloseAction);
begin
  WSClient.Active := False;
end;

procedure TfrmWebSocketClient.KRAKEN_FUTURESKrakenFuturesConnect
  (Sender: TObject; Version: string);
begin
  DoLog('#connected Kraken Futures');
end;

procedure TfrmWebSocketClient.KRAKEN_FUTURESKrakenFuturesError(Sender: TObject;
  Error: string);
begin
  DoLog('#error: ' + Error);
end;

procedure TfrmWebSocketClient.KRAKEN_FUTURESKrakenFuturesSubscribed
  (Sender: TObject; Feed, ProductId: string);
begin
  DoLog('#subscribed: ' + Feed + ' ' + ProductId);
end;

procedure TfrmWebSocketClient.KRAKEN_FUTURESKrakenFuturesUnSubscribed
  (Sender: TObject; Feed, ProductId: string);
begin
  DoLog('#unsubscribed: ' + Feed + ' ' + ProductId);
end;

procedure TfrmWebSocketClient.KRAKEN_FUTURESKrakenHTTPException(Sender: TObject;
  E: Exception);
begin
  DoLog('#exception: ' + E.Message);
end;

procedure TfrmWebSocketClient.MQTTMQTTBeforeConnect
  (Connection: TsgcWSConnection; var aCleanSession: Boolean;
  var aClientIdentifier: string);
begin
  if FMQTTClientId <> '' then
  begin
    aClientIdentifier := FMQTTClientId;
    FMQTTClientId := '';
  end;
end;

procedure TfrmWebSocketClient.MQTTMQTTConnect(Connection: TsgcWSConnection;
  const Session: Boolean; const ReasonCode: Integer; const ReasonName: string;
  const ConnectProperties: TsgcWSMQTTCONNACKProperties);
begin
  DoLog('#connected');
  chkTLS.Enabled := False;
  chkCompressed.Enabled := False;
  if FMQTTSubscribeTopic <> '' then
  begin
    MQTT.Subscribe(FMQTTSubscribeTopic);
    FMQTTSubscribeTopic := '';
  end;
end;

procedure TfrmWebSocketClient.MQTTMQTTDisconnect(Connection: TsgcWSConnection;
  ReasonCode: Integer; const ReasonName: string;
  DisconnectProperties: TsgcWSMQTTDISCONNECTProperties);
begin
  DoLog('#disconnected');
  chkTLS.Enabled := True;
  chkCompressed.Enabled := True;
end;

procedure TfrmWebSocketClient.MQTTMQTTPing(Connection: TsgcWSConnection);
begin
  DoLog('#ping');
end;

procedure TfrmWebSocketClient.MQTTMQTTPubAck(Connection: TsgcWSConnection;
  aPacketIdentifier: Word; ReasonCode: Integer; const ReasonName: string;
  PubAckProperties: TsgcWSMQTTPUBACKProperties);
begin
  DoLog('#PubAck: ' + IntToStr(aPacketIdentifier));
end;

procedure TfrmWebSocketClient.MQTTMQTTPubComp(Connection: TsgcWSConnection;
  aPacketIdentifier: Word; ReasonCode: Integer; const ReasonName: string;
  PubCompProperties: TsgcWSMQTTPUBCOMPProperties);
begin
  DoLog('#PubComp: ' + IntToStr(aPacketIdentifier));
end;

procedure TfrmWebSocketClient.MQTTMQTTPublish(Connection: TsgcWSConnection;
  aTopic, aText: string; PublishProperties: TsgcWSMQTTPublishProperties);
begin
  DoLog(aTopic + ': ' + aText);
end;

procedure TfrmWebSocketClient.MQTTMQTTPubRec(Connection: TsgcWSConnection;
  aPacketIdentifier: Word; ReasonCode: Integer; const ReasonName: string;
  PubRecProperties: TsgcWSMQTTPUBRECProperties);
begin
  DoLog('#PubRec: ' + IntToStr(aPacketIdentifier));
end;

procedure TfrmWebSocketClient.MQTTMQTTSubscribe(Connection: TsgcWSConnection;
  aPacketIdentifier: Word; aCodes: TsgcWSSUBACKS;
  SubscribeProperties: TsgcWSMQTTSUBACKProperties);
begin
  DoLog('#Subscribe: ' + IntToStr(aPacketIdentifier));
end;

procedure TfrmWebSocketClient.MQTTMQTTUnSubscribe(Connection: TsgcWSConnection;
  aPacketIdentifier: Word; aCodes: TsgcWSUNSUBACKS;
  UnsubscribeProperties: TsgcWSMQTTUNSUBACKProperties);
begin
  DoLog('#UnSubscribe: ' + IntToStr(aPacketIdentifier));
end;

procedure TfrmWebSocketClient.PUSHERDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;

procedure TfrmWebSocketClient.PUSHERPusherConnect(Sender: TObject;
  Socket_id: string; Timeout: Integer);
begin
  DoLog('#connected');
end;

procedure TfrmWebSocketClient.PUSHERPusherError(Sender: TObject; Code: Integer;
  Msg: string);
begin
  DoLog('#error: ' + IntToStr(Code) + ' ' + Msg);
end;

procedure TfrmWebSocketClient.PUSHERPusherEvent(Sender: TObject;
  Event, Channel, Data: string);
begin
  DoLog(Event + ' ' + Channel + ' ' + Data);
end;

procedure TfrmWebSocketClient.PUSHERPusherSubscribe(Sender: TObject;
  Channel, Data: string);
begin
  DoLog('#subscribed: ' + Channel + ' ' + Data);
end;

procedure TfrmWebSocketClient.PUSHERPusherMemberAdded(Sender: TObject;
  Channel, UserId, UserInfo: string);
begin
  DoLog('#member added: ' + Channel + ' UserId=' + UserId + ' ' + UserInfo);
end;

procedure TfrmWebSocketClient.PUSHERPusherMemberRemoved(Sender: TObject;
  Channel, UserId, UserInfo: string);
begin
  DoLog('#member removed: ' + Channel + ' UserId=' + UserId + ' ' + UserInfo);
end;

procedure TfrmWebSocketClient.PUSHERPusherSubscriptionCount(Sender: TObject;
  Channel: string; SubscriptionCount: Integer);
begin
  DoLog('#subscription count: ' + Channel + ' Count=' + IntToStr(SubscriptionCount));
end;

procedure TfrmWebSocketClient.PUSHERPusherCacheMiss(Sender: TObject;
  Channel: string);
begin
  DoLog('#cache miss: ' + Channel);
end;

procedure TfrmWebSocketClient.btnPUSHERBatchEventsClick(Sender: TObject);
begin
  DoLog(PUSHER.TriggerBatchEvents(txtPUSHERBatchREST.Text));
end;

procedure TfrmWebSocketClient.btnPUSHERTerminateUserClick(Sender: TObject);
begin
  DoLog(PUSHER.TerminateUserConnections(txtPUSHERUserIdREST.Text));
end;

procedure TfrmWebSocketClient.SIGNALRCORESignalRCoreCancelInvocation
  (Sender: TObject; CancelInvocation: TSignalRCore_CancelInvocation);
begin
  DoLog('#Cancel Invocation: ' + CancelInvocation.InvocationId);
end;

procedure TfrmWebSocketClient.SIGNALRCORESignalRCoreClose(Sender: TObject;
  Close: TSignalRCore_Close);
begin
  DoLog('#closed: ' + Close.Error);
end;

procedure TfrmWebSocketClient.SIGNALRCORESignalRCoreCompletion(Sender: TObject;
  Completion: TSignalRCore_Completion);
begin
  DoLog('#Completion: ' + Completion.Result + ' ' + Completion.Error);
end;

procedure TfrmWebSocketClient.SIGNALRCORESignalRCoreConnect(Sender: TObject;
  Connect: TSignalRCore_Connect);
begin
  DoLog('#connected: ' + Connect.ConnectionId);
end;

procedure TfrmWebSocketClient.SIGNALRCORESignalRCoreDisconnect(Sender: TObject;
  CloseCode: Integer; CloseReason: string);
begin
  DoLog('#disconnected: ' + IntToStr(CloseCode) + ' ' + CloseReason);
end;

procedure TfrmWebSocketClient.SIGNALRCORESignalRCoreError(Sender: TObject;
  Error: TSignalRCore_Error);
begin
  DoLog('#error: ' + Error.Error);
end;

procedure TfrmWebSocketClient.SIGNALRCORESignalRCoreInvocation(Sender: TObject;
  Invocation: TSignalRCore_Invocation);
begin
  DoLog('#Invocation: ' + Invocation.Target + ' ' + Invocation.Arguments);
end;

procedure TfrmWebSocketClient.SIGNALRCORESignalRCoreKeepAlive(Sender: TObject);
begin
  DoLog('#keepalive');
end;

procedure TfrmWebSocketClient.SIGNALRCORESignalRCoreStreamInvocation
  (Sender: TObject; StreamInvocation: TSignalRCore_Invocation);
begin
  DoLog('#stream invocation: ' + StreamInvocation.Target + ' ' +
    StreamInvocation.Arguments);
end;

procedure TfrmWebSocketClient.SIGNALRCORESignalRCoreStreamItem(Sender: TObject;
  StreamItem: TSignalRCore_StreamItem; var Cancel: Boolean);
begin
  DoLog('#stream item: ' + StreamItem.Item);
end;

procedure TfrmWebSocketClient.SIGNALRSignalRConnect(Sender: TObject;
  MessageId, aData: string);
begin
  DoLog('#connected');
end;

procedure TfrmWebSocketClient.SIGNALRSignalRDisconnect(Sender: TObject;
  aCloseCode: Integer);
begin
  DoLog('#disconnected');
end;

procedure TfrmWebSocketClient.SIGNALRSignalRError(Sender: TObject;
  Error: string);
begin
  DoLog('#error: ' + Error);
end;

procedure TfrmWebSocketClient.SIGNALRSignalRKeepAlive(Sender: TObject);
begin
  DoLog('#keepalive');
end;

procedure TfrmWebSocketClient.SIGNALRSignalRMessage(Sender: TObject;
  MessageId, aData: string);
begin
  DoLog('[' + MessageId + '] ' + aData);
end;

procedure TfrmWebSocketClient.SIGNALRSignalRResult(Sender: TObject;
  InvocationId, Result, Error: string);
begin
  DoLog('[' + InvocationId + '] ' + Result + ' ' + Error);
end;

procedure TfrmWebSocketClient.STOMPRabbitMQConnected
  (Connection: TsgcWSConnection; Headers: TsgcWSRabbitMQSTOMPHeadersConnected);
begin
  DoLog('#connected');
end;

procedure TfrmWebSocketClient.STOMPRabbitMQDisconnected
  (Connection: TsgcWSConnection; Code: Integer);
begin
  DoLog('#disconnected');
end;

procedure TfrmWebSocketClient.STOMPRabbitMQError(Connection: TsgcWSConnection;
  MessageText: string; Headers: TsgcWSRabbitMQSTOMPHeadersError);
begin
  DoLog('#error: ' + MessageText);
end;

procedure TfrmWebSocketClient.STOMPRabbitMQMessage(Connection: TsgcWSConnection;
  MessageText: string; Headers: TsgcWSRabbitMQSTOMPHeadersMessage;
  Subscription: TsgcWSBrokerSTOMPSubscriptionItem);
begin
  DoLog(MessageText);
end;

procedure TfrmWebSocketClient.tabAWSAppSyncShow(Sender: TObject);
begin
  DoServerAWSAppSync;
end;

procedure TfrmWebSocketClient.tabDiscordShow(Sender: TObject);
begin
  DoServerDISCORD;
end;

procedure TfrmWebSocketClient.tabMQTTShow(Sender: TObject);
begin
  DoServerMQTT(0);
end;

procedure TfrmWebSocketClient.tabPUSHERShow(Sender: TObject);
begin
  DoServerPUSHER;
end;

procedure TfrmWebSocketClient.tabSIGNALRCOREShow(Sender: TObject);
begin
  DoServerSIGNALRCORE(0);
end;

procedure TfrmWebSocketClient.tabSIGNALRShow(Sender: TObject);
begin
  DoServerSIGNALR;
end;

procedure TfrmWebSocketClient.tabSOCKETIOShow(Sender: TObject);
begin
  DoServerSOCKETIO;
end;

procedure TfrmWebSocketClient.tabSTOMPShow(Sender: TObject);
begin
  DoServerSTOMP(0);
end;

procedure TfrmWebSocketClient.tabWebSocketShow(Sender: TObject);
begin
  DoServerWebSocket(cboServerWebSocket.itemIndex);
end;

procedure TfrmWebSocketClient.txtDiscordBotTokenChange(Sender: TObject);
begin
  DoServerDISCORD;
end;

procedure TfrmWebSocketClient.WSClientConnect(Connection: TsgcWSConnection);
var
  vText: string;
begin
  DoLog('#connected');

  vText := TsgcWSConnectionClient(Connection).ALPNProtocol;
end;

procedure TfrmWebSocketClient.WSClientDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;

procedure TfrmWebSocketClient.WSClientError(Connection: TsgcWSConnection;
  const Error: string);
begin
  DoLog('#error: ' + Error);
end;

procedure TfrmWebSocketClient.WSClientException(Connection: TsgcWSConnection;
  E: Exception);
begin
  DoLog('#exception: ' + E.Message);
end;

procedure TfrmWebSocketClient.WSClientMessage(Connection: TsgcWSConnection;
  const Text: string);
begin
  DoLog(Text);
end;

end.
```

