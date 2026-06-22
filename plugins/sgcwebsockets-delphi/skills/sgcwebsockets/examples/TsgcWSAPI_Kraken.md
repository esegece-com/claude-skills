# TsgcWSAPI_Kraken - Example

Full source of `uKraken.pas` from the **05.Crypto/08.Kraken** demo, which uses `TsgcWSAPI_Kraken`.

API reference: [TsgcWSAPI_Kraken](../reference/api/TsgcWSAPI_Kraken.md)
Source demo: `05.Crypto/08.Kraken` (file `uKraken.pas`)

```pascal
unit uKraken;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_Kraken, sgcHTTP_API_Kraken;

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
    pnlMemo: TPanel;
    Label14: TLabel;
    txtParameters: TEdit;
    chkOverWebSocket: TCheckBox;
    tabKRAKEN: TTabSheet;
    KRAKEN: TsgcWSAPI_Kraken;
    Pair: TLabel;
    txtKrakenPair: TEdit;
    btnKrakenSubscribeTicker: TButton;
    btnKrakenUnSubscribeTicker: TButton;
    cboKrakenInterval: TComboBox;
    cboKrakenDepth: TComboBox;
    btnKrakenUnSubscribeOHLC: TButton;
    btnKrakenSubscribeOHLC: TButton;
    btnKrakenSubscribeTrade: TButton;
    btnKrakenUnSubscribeTrade: TButton;
    btnKrakenUnSubscribeBook: TButton;
    btnKrakenSubscribeBook: TButton;
    btnKrakenSubscribeSpread: TButton;
    btnKrakenUnSubscribeSpread: TButton;
    btnKrakenSubscribeAll: TButton;
    btnKrakenUnSubscribeAll: TButton;
    Label48: TLabel;
    Label49: TLabel;
    txtKrakenApiKey: TEdit;
    txtKrakenApiSecret: TEdit;
    pageKraken: TPageControl;
    tabKrakenWebSocketsPublicAPI: TTabSheet;
    tabKrakenWebSocketsPrivateAPI: TTabSheet;
    btnKrakenSubscribeOwnTrades: TButton;
    btnKrakenUnSubscribeOwnTrades: TButton;
    btnKrakenSubscribeOpenOrders: TButton;
    btnKrakenUnSubscribeOpenOrders: TButton;
    btnKrakenCancelOrder: TButton;
    txtKrakenOrderId: TEdit;
    tabKrakenRESTPublicAPI: TTabSheet;
    btnKrakenGetServerTime: TButton;
    btnKrakenGetAssets: TButton;
    btnKrakenGetAssetsPairs: TButton;
    btnKrakenGetTicker: TButton;
    btnKrakenGetOHLC: TButton;
    btnKrakenGetOrderBook: TButton;
    Label50: TLabel;
    txtKrakenRESTPair: TEdit;
    btnKrakenGetTrades: TButton;
    btnKrakenGetSpread: TButton;
    btnKrakenGetSystemStatus: TButton;
    tabKrakenRESTPrivateAPI: TTabSheet;
    btnKrakenGetAccountBalance: TButton;
    btnKrakenGetTradeBalance: TButton;
    btnKrakenGetOpenOrders: TButton;
    btnKrakenGetClosedOrders: TButton;
    btnKrakenGetTradesHistory: TButton;
    btnKrakenGetLedgers: TButton;
    btnKrakenGetTradeVolume: TButton;
    btnKrakenCancelAllOrders: TButton;
    btnKrakenGetExtendedBalance: TButton;
    btnKrakenGetWithdrawalMethods: TButton;
    tabKrakenRESTPrivateTrading: TTabSheet;
    btnKrakenRESTCancelOrder: TButton;
    txtKrakenRESTOrderId: TEdit;
    PageControlKraken: TPageControl;
    tabKrakenStocks: TTabSheet;
    tabKrakenFutures: TTabSheet;
    pageKrakenFutures: TPageControl;
    tabKrakenFuturesWebSocketsPublicAPI: TTabSheet;
    btnKrakenFuturesSubscribeBook: TButton;
    btnKrakenFuturesSubscribeHeartbeat: TButton;
    btnKrakenFuturesSubscribeTickerLite: TButton;
    btnKrakenFuturesSubscribeTicker: TButton;
    btnKrakenFuturesSubscribeTrade: TButton;
    btnKrakenFuturesUnSubscribeBook: TButton;
    btnKrakenFuturesUnSubscribeHeartbeat: TButton;
    btnKrakenFuturesUnSubscribeTickerLite: TButton;
    btnKrakenFuturesUnSubscribeTicker: TButton;
    btnKrakenFuturesUnSubscribeTrade: TButton;
    tabKrakenFuturesWebSocketsPrivateAPI: TTabSheet;
    btnKrakenFuturesSubscribeOpenOrdersVerbose: TButton;
    btnKrakenFuturesUnSubscribeOpenOrdersVerbose: TButton;
    btnKrakenFuturesSubscribeOpenPositions: TButton;
    btnKrakenFuturesUnSubscribeOpenPositions: TButton;
    TabSheet3: TTabSheet;
    btnKrakenFuturesRestPublicGetFeeSchedules: TButton;
    btnKrakenFuturesRestPublicGetInstruments: TButton;
    btnKrakenFuturesRestPublicGetOrderBook: TButton;
    btnKrakenFuturesRestPublicGetHistory: TButton;
    btnKrakenFuturesRestPublicGetTickers: TButton;
    TabSheet4: TTabSheet;
    btnKrakenFuturesRestPrivateGetAccounts: TButton;
    btnKrakenFuturesRestPrivateGetNotifications: TButton;
    btnKrakenFuturesRestPrivateCancelAllOrders: TButton;
    btnKrakenFuturesRestPrivateGetOpenOrders: TButton;
    btnKrakenFuturesRestPrivateGetHistoricalExecutions: TButton;
    btnKrakenFuturesRestPrivateGetHistoricalOrders: TButton;
    btnKrakenFuturesRestPrivateGetHistoricalTriggers: TButton;
    KRAKEN_FUTURES: TsgcWSAPI_Kraken_Futures;
    btnKrakenFuturesSubscribeAccountLog: TButton;
    btnKrakenFuturesUnSubscribeAccountLog: TButton;
    btnKrakenFuturesUnSubscribeFills: TButton;
    btnKrakenFuturesSubscribeFills: TButton;
    btnKrakenFuturesSubscribeOpenOrders: TButton;
    btnKrakenFuturesUnSubscribeOpenOrders: TButton;
    btnKrakenFuturesSubscribeAccountBalance: TButton;
    btnKrakenFuturesUnSubscribeAccountBalance: TButton;
    btnKrakenFuturesSubscribeNotifications: TButton;
    btnKrakenFuturesUnSubscribeNotifications: TButton;
    btnKrakenFuturesRestPrivateGetOpenPositions: TButton;
    btnKrakenFuturesRestPrivateGetFills: TButton;
    Label64: TLabel;
    Label65: TLabel;
    txtKrakenFuturesMarketOrderSize: TEdit;
    cboKrakenFuturesMarketOrderSide: TComboBox;
    btnKrakenFuturesMarketOrder: TButton;
    Label66: TLabel;
    Label67: TLabel;
    Label68: TLabel;
    btnKrakenFuturesLimitOrder: TButton;
    txtKrakenFuturesLimitOrderPrice: TEdit;
    txtKrakenFuturesLimitOrderSize: TEdit;
    cboKrakenFuturesLimitOrderSide: TComboBox;
    chkKrakenFuturesDemo: TCheckBox;
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnKrakenCancelOrderClick(Sender: TObject);
    procedure btnKrakenGetAccountBalanceClick(Sender: TObject);
    procedure btnKrakenGetAssetsClick(Sender: TObject);
    procedure btnKrakenGetAssetsPairsClick(Sender: TObject);
    procedure btnKrakenGetClosedOrdersClick(Sender: TObject);
    procedure btnKrakenGetLedgersClick(Sender: TObject);
    procedure btnKrakenGetServerTimeClick(Sender: TObject);
    procedure btnKrakenGetTickerClick(Sender: TObject);
    procedure btnKrakenSubscribeAllClick(Sender: TObject);
    procedure btnKrakenSubscribeOHLCClick(Sender: TObject);
    procedure btnKrakenSubscribeTickerClick(Sender: TObject);
    procedure btnKrakenSubscribeTradeClick(Sender: TObject);
    procedure btnKrakenUnSubscribeOHLCClick(Sender: TObject);
    procedure btnKrakenUnSubscribeTickerClick(Sender: TObject);
    procedure btnKrakenUnSubscribeTradeClick(Sender: TObject);
    procedure btnKrakenSubscribeBookClick(Sender: TObject);
    procedure btnKrakenUnSubscribeAllClick(Sender: TObject);
    procedure btnKrakenUnSubscribeBookClick(Sender: TObject);
    procedure btnKrakenUnSubscribeSpreadClick(Sender: TObject);
    procedure btnKrakenSubscribeOwnTradesClick(Sender: TObject);
    procedure btnKrakenUnSubscribeOwnTradesClick(Sender: TObject);
    procedure btnKrakenSubscribeOpenOrdersClick(Sender: TObject);
    procedure btnKrakenUnSubscribeOpenOrdersClick(Sender: TObject);
    procedure btnKrakenGetOHLCClick(Sender: TObject);
    procedure btnKrakenGetOpenOrdersClick(Sender: TObject);
    procedure btnKrakenGetOrderBookClick(Sender: TObject);
    procedure btnKrakenGetSpreadClick(Sender: TObject);
    procedure btnKrakenGetSystemStatusClick(Sender: TObject);
    procedure btnKrakenCancelAllOrdersClick(Sender: TObject);
    procedure btnKrakenGetExtendedBalanceClick(Sender: TObject);
    procedure btnKrakenGetWithdrawalMethodsClick(Sender: TObject);
    procedure btnKrakenGetTradeBalanceClick(Sender: TObject);
    procedure btnKrakenGetTradesClick(Sender: TObject);
    procedure btnKrakenGetTradesHistoryClick(Sender: TObject);
    procedure btnKrakenGetTradeVolumeClick(Sender: TObject);
    procedure btnKrakenRESTCancelOrderClick(Sender: TObject);
    procedure btnKrakenFuturesMarketOrderClick(Sender: TObject);
    procedure btnKrakenFuturesRestPrivateCancelAllOrdersClick(Sender: TObject);
    procedure btnKrakenFuturesRestPrivateGetAccountsClick(Sender: TObject);
    procedure btnKrakenFuturesRestPrivateGetFillsClick(Sender: TObject);
    procedure btnKrakenFuturesRestPrivateGetHistoricalExecutionsClick
      (Sender: TObject);
    procedure btnKrakenFuturesRestPrivateGetHistoricalOrdersClick
      (Sender: TObject);
    procedure btnKrakenFuturesRestPrivateGetHistoricalTriggersClick
      (Sender: TObject);
    procedure btnKrakenFuturesRestPrivateGetNotificationsClick(Sender: TObject);
    procedure btnKrakenFuturesRestPrivateGetOpenOrdersClick(Sender: TObject);
    procedure btnKrakenFuturesRestPrivateGetOpenPositionsClick(Sender: TObject);
    procedure btnKrakenFuturesRestPublicGetFeeSchedulesClick(Sender: TObject);
    procedure btnKrakenFuturesRestPublicGetHistoryClick(Sender: TObject);
    procedure btnKrakenFuturesRestPublicGetInstrumentsClick(Sender: TObject);
    procedure btnKrakenFuturesRestPublicGetOrderBookClick(Sender: TObject);
    procedure btnKrakenFuturesRestPublicGetTickersClick(Sender: TObject);
    procedure btnKrakenFuturesSubscribeAccountBalanceClick(Sender: TObject);
    procedure btnKrakenFuturesSubscribeAccountLogClick(Sender: TObject);
    procedure btnKrakenFuturesSubscribeBookClick(Sender: TObject);
    procedure btnKrakenFuturesSubscribeFillsClick(Sender: TObject);
    procedure btnKrakenFuturesSubscribeHeartbeatClick(Sender: TObject);
    procedure btnKrakenFuturesSubscribeNotificationsClick(Sender: TObject);
    procedure btnKrakenFuturesSubscribeOpenOrdersClick(Sender: TObject);
    procedure btnKrakenFuturesSubscribeOpenOrdersVerboseClick(Sender: TObject);
    procedure btnKrakenFuturesSubscribeOpenPositionsClick(Sender: TObject);
    procedure btnKrakenFuturesSubscribeTickerClick(Sender: TObject);
    procedure btnKrakenFuturesSubscribeTickerLiteClick(Sender: TObject);
    procedure btnKrakenFuturesSubscribeTradeClick(Sender: TObject);
    procedure btnKrakenFuturesUnSubscribeAccountBalanceClick(Sender: TObject);
    procedure btnKrakenFuturesUnSubscribeAccountLogClick(Sender: TObject);
    procedure btnKrakenFuturesUnSubscribeBookClick(Sender: TObject);
    procedure btnKrakenFuturesUnSubscribeFillsClick(Sender: TObject);
    procedure btnKrakenFuturesUnSubscribeHeartbeatClick(Sender: TObject);
    procedure btnKrakenFuturesUnSubscribeNotificationsClick(Sender: TObject);
    procedure btnKrakenFuturesUnSubscribeOpenOrdersClick(Sender: TObject);
    procedure btnKrakenFuturesUnSubscribeOpenOrdersVerboseClick
      (Sender: TObject);
    procedure btnKrakenFuturesUnSubscribeOpenPositionsClick(Sender: TObject);
    procedure btnKrakenFuturesUnSubscribeTickerClick(Sender: TObject);
    procedure btnKrakenFuturesUnSubscribeTickerLiteClick(Sender: TObject);
    procedure btnKrakenFuturesUnSubscribeTradeClick(Sender: TObject);
    procedure btnKrakenSubscribeSpreadClick(Sender: TObject);
    procedure btnKrakenFuturesLimitOrderClick(Sender: TObject);
    procedure chkKrakenFuturesDemoClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure KRAKENConnect(Connection: TsgcWSConnection);
    procedure KRAKENDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure KRAKENKrakenConnect(Sender: TObject;
      ConnectionId, Status, Version: string);
    procedure KRAKENKrakenData(Sender: TObject; aData: string);
    procedure KRAKENKrakenHTTPException(Sender: TObject; E: Exception);
    procedure KRAKENKrakenSubscribed(Sender: TObject; ChannelId: Integer;
      Pair, Subscription, ChannelName: string; ReqID: Integer);
    procedure KRAKENKrakenSubscriptionError(Sender: TObject;
      ErrorMessage, Pair, Subscription: string; ReqID: Integer);
    procedure KRAKENKrakenSystemStatus(Sender: TObject;
      ConnectionId, Status, Version: string);
    procedure KRAKENKrakenUnSubscribed(Sender: TObject; ChannelId: Integer;
      Pair, Subscription: string; ReqID: Integer);
    procedure KRAKEN_FUTURESConnect(Connection: TsgcWSConnection);
    procedure KRAKEN_FUTURESDisconnect(Connection: TsgcWSConnection;
      Code: Integer);
    procedure KRAKEN_FUTURESKrakenData(Sender: TObject; aData: string);
    procedure KRAKEN_FUTURESKrakenFuturesConnect(Sender: TObject;
      Version: string);
    procedure KRAKEN_FUTURESKrakenFuturesError(Sender: TObject; Error: string);
    procedure KRAKEN_FUTURESKrakenFuturesSubscribed(Sender: TObject;
      Feed, ProductId: string);
    procedure KRAKEN_FUTURESKrakenFuturesUnSubscribed(Sender: TObject;
      Feed, ProductId: string);
    procedure KRAKEN_FUTURESKrakenHTTPException(Sender: TObject; E: Exception);
    procedure tabKrakenFuturesShow(Sender: TObject);
    procedure tabKRAKENShow(Sender: TObject);
    procedure tabKrakenStocksShow(Sender: TObject);
    procedure txtKrakenApiKeyChange(Sender: TObject);
    procedure txtKrakenApiSecretChange(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
    procedure DoBeforeConnectKraken;
  private
    procedure DoServerKRAKEN;
    procedure DoServerKRAKENFUT;
  end;

var
  frmWebSocketClient: TfrmWebSocketClient;

implementation

uses
  sgcWebSocket_Helpers, sgcJSON, StrUtils, sgcBase_Helpers,
  ShellAPI, DateUtils;
{$R *.dfm}

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


procedure TfrmWebSocketClient.btnKrakenCancelOrderClick(Sender: TObject);
begin
  KRAKEN.CancelOrder(txtKrakenOrderId.Text);
end;


procedure TfrmWebSocketClient.btnKrakenGetAccountBalanceClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetAccountBalance);
end;


procedure TfrmWebSocketClient.btnKrakenGetAssetsClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetAssets);
end;


procedure TfrmWebSocketClient.btnKrakenGetAssetsPairsClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetAssetPairs([txtKrakenRESTPair.Text]));
end;


procedure TfrmWebSocketClient.btnKrakenGetClosedOrdersClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetClosedOrders());
end;


procedure TfrmWebSocketClient.btnKrakenGetLedgersClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetLedgers);
end;


procedure TfrmWebSocketClient.btnKrakenGetServerTimeClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetServerTime);
end;


procedure TfrmWebSocketClient.btnKrakenGetTickerClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetTicker([txtKrakenRESTPair.Text]));
end;


procedure TfrmWebSocketClient.btnKrakenSubscribeAllClick(Sender: TObject);
begin
  KRAKEN.SubscribeAll([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenSubscribeOHLCClick(Sender: TObject);
begin
  KRAKEN.SubscribeOHLC([txtKrakenPair.Text],
    TsgcWSKrakenInterval(cboKrakenInterval.itemIndex));
end;


procedure TfrmWebSocketClient.btnKrakenSubscribeTickerClick(Sender: TObject);
begin
  KRAKEN.SubscribeTicker([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenSubscribeTradeClick(Sender: TObject);
begin
  KRAKEN.SubscribeTrade([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenUnSubscribeOHLCClick(Sender: TObject);
begin
  KRAKEN.UnSubscribeOHLC([txtKrakenPair.Text],
    TsgcWSKrakenInterval(cboKrakenInterval.itemIndex));
end;


procedure TfrmWebSocketClient.btnKrakenUnSubscribeTickerClick(Sender: TObject);
begin
  KRAKEN.UnSubscribeTicker([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenUnSubscribeTradeClick(Sender: TObject);
begin
  KRAKEN.UnSubscribeTrade([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenSubscribeBookClick(Sender: TObject);
begin
  KRAKEN.SubscribeBook([txtKrakenPair.Text],
    TsgcWSKrakenDepth(cboKrakenDepth.itemIndex));
end;


procedure TfrmWebSocketClient.btnKrakenUnSubscribeAllClick(Sender: TObject);
begin
  KRAKEN.UnSubscribeAll([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenUnSubscribeBookClick(Sender: TObject);
begin
  KRAKEN.UnSubscribeBook([txtKrakenPair.Text],
    TsgcWSKrakenDepth(cboKrakenDepth.itemIndex));
end;


procedure TfrmWebSocketClient.btnKrakenUnSubscribeSpreadClick(Sender: TObject);
begin
  KRAKEN.UnSubscribeSpread([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenSubscribeOwnTradesClick(Sender: TObject);
begin
  KRAKEN.SubscribeOwnTrades;
end;


procedure TfrmWebSocketClient.btnKrakenUnSubscribeOwnTradesClick
  (Sender: TObject);
begin
  KRAKEN.UnSubscribeOwnTrades;
end;


procedure TfrmWebSocketClient.btnKrakenSubscribeOpenOrdersClick
  (Sender: TObject);
begin
  KRAKEN.SubscribeOpenOrders;
end;


procedure TfrmWebSocketClient.btnKrakenUnSubscribeOpenOrdersClick
  (Sender: TObject);
begin
  KRAKEN.UnSubscribeOpenOrders;
end;


procedure TfrmWebSocketClient.btnKrakenGetOHLCClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetOHLC(txtKrakenRESTPair.Text));
end;


procedure TfrmWebSocketClient.btnKrakenGetOpenOrdersClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetOpenOrders);
end;


procedure TfrmWebSocketClient.btnKrakenGetOrderBookClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetOrderBook(txtKrakenRESTPair.Text));
end;


procedure TfrmWebSocketClient.btnKrakenGetSpreadClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetSpread(txtKrakenRESTPair.Text));
end;


procedure TfrmWebSocketClient.btnKrakenGetSystemStatusClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetSystemStatus);
end;


procedure TfrmWebSocketClient.btnKrakenCancelAllOrdersClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.CancelAllOrders);
end;


procedure TfrmWebSocketClient.btnKrakenGetExtendedBalanceClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetExtendedBalance);
end;


procedure TfrmWebSocketClient.btnKrakenGetWithdrawalMethodsClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetWithdrawalMethods);
end;


procedure TfrmWebSocketClient.btnKrakenGetTradeBalanceClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetTradeBalance);
end;


procedure TfrmWebSocketClient.btnKrakenGetTradesClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetTrades(txtKrakenRESTPair.Text));
end;


procedure TfrmWebSocketClient.btnKrakenGetTradesHistoryClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetTradesHistory);
end;


procedure TfrmWebSocketClient.btnKrakenGetTradeVolumeClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.GetTradeVolume);
end;


procedure TfrmWebSocketClient.btnKrakenRESTCancelOrderClick(Sender: TObject);
begin
  DoLog(KRAKEN.REST_API.CancelOrder(txtKrakenRESTOrderId.Text));
end;


procedure TfrmWebSocketClient.btnKrakenFuturesMarketOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPKrakenFuturesOrderSide;
begin
  if cboKrakenFuturesMarketOrderSide.itemIndex = 0 then
    vSide := kosfBuy
  else
    vSide := kosfSell;

  DoLog(KRAKEN_FUTURES.REST_API.SendMarketOrder(vSide, txtKrakenRESTPair.Text,
    StrToInt(txtKrakenFuturesMarketOrderSize.Text)));
end;


procedure TfrmWebSocketClient.btnKrakenFuturesRestPrivateCancelAllOrdersClick
  (Sender: TObject);
begin
  DoLog(KRAKEN_FUTURES.REST_API.CancelAllOrders(txtKrakenRESTPair.Text));
end;


procedure TfrmWebSocketClient.btnKrakenFuturesRestPrivateGetAccountsClick
  (Sender: TObject);
begin
  DoLog(KRAKEN_FUTURES.REST_API.GetAccounts);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesRestPrivateGetFillsClick
  (Sender: TObject);
begin
  DoLog(KRAKEN_FUTURES.REST_API.GetFills);
end;


procedure TfrmWebSocketClient.
  btnKrakenFuturesRestPrivateGetHistoricalExecutionsClick(Sender: TObject);
begin
  DoLog(KRAKEN_FUTURES.REST_API.GetHistoricalExecutions(IncDay(Now, -30)));
end;


procedure TfrmWebSocketClient.
  btnKrakenFuturesRestPrivateGetHistoricalOrdersClick(Sender: TObject);
begin
  DoLog(KRAKEN_FUTURES.REST_API.GetHistoricalOrders(IncDay(Now, -30)));
end;


procedure TfrmWebSocketClient.
  btnKrakenFuturesRestPrivateGetHistoricalTriggersClick(Sender: TObject);
begin
  DoLog(KRAKEN_FUTURES.REST_API.GetHistoricalTriggers(IncDay(Now, -30)));
end;


procedure TfrmWebSocketClient.btnKrakenFuturesRestPrivateGetNotificationsClick
  (Sender: TObject);
begin
  DoLog(KRAKEN_FUTURES.REST_API.GetNotifications);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesRestPrivateGetOpenOrdersClick
  (Sender: TObject);
begin
  DoLog(KRAKEN_FUTURES.REST_API.GetOpenOrders);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesRestPrivateGetOpenPositionsClick
  (Sender: TObject);
begin
  DoLog(KRAKEN_FUTURES.REST_API.GetOpenPositions);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesRestPublicGetFeeSchedulesClick
  (Sender: TObject);
begin
  DoLog(KRAKEN_FUTURES.REST_API.GetFeeSchedules);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesRestPublicGetHistoryClick
  (Sender: TObject);
begin
  DoLog(KRAKEN_FUTURES.REST_API.GetHistory(txtKrakenRESTPair.Text));
end;


procedure TfrmWebSocketClient.btnKrakenFuturesRestPublicGetInstrumentsClick
  (Sender: TObject);
begin
  DoLog(KRAKEN_FUTURES.REST_API.GetInstruments);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesRestPublicGetOrderBookClick
  (Sender: TObject);
begin
  DoLog(KRAKEN_FUTURES.REST_API.GetOrderBook(txtKrakenRESTPair.Text));
end;


procedure TfrmWebSocketClient.btnKrakenFuturesRestPublicGetTickersClick
  (Sender: TObject);
begin
  DoLog(KRAKEN_FUTURES.REST_API.GetTickers);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesSubscribeAccountBalanceClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.SubscribeAccountBalanceAndMargins;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesSubscribeAccountLogClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.SubscribeAccountLog;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesSubscribeBookClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.SubscribeBook([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesSubscribeFillsClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.SubscribeFills;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesSubscribeHeartbeatClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.SubscribeHeartBeat;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesSubscribeNotificationsClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.SubscribeNotifications;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesSubscribeOpenOrdersClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.SubscribeOpenOrders;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesSubscribeOpenOrdersVerboseClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.SubscribeOpenOrdersVerbose;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesSubscribeOpenPositionsClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.SubscribeOpenPositions;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesSubscribeTickerClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.SubscribeTicker([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesSubscribeTickerLiteClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.SubscribeTickerLite([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesSubscribeTradeClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.SubscribeTrade([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesUnSubscribeAccountBalanceClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.UnSubscribeAccountBalanceAndMargins;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesUnSubscribeAccountLogClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.UnSubscribeAccountLog;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesUnSubscribeBookClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.UnSubscribeBook([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesUnSubscribeFillsClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.UnSubscribeFills;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesUnSubscribeHeartbeatClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.UnSubscribeHeartBeat;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesUnSubscribeNotificationsClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.UnSubscribeNotifications;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesUnSubscribeOpenOrdersClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.UnSubscribeOpenOrders;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesUnSubscribeOpenOrdersVerboseClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.UnSubscribeOpenOrdersVerbose;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesUnSubscribeOpenPositionsClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.UnSubscribeOpenPositions;
end;


procedure TfrmWebSocketClient.btnKrakenFuturesUnSubscribeTickerClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.UnSubscribeTicker([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesUnSubscribeTickerLiteClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.UnSubscribeTickerLite([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesUnSubscribeTradeClick
  (Sender: TObject);
begin
  KRAKEN_FUTURES.UnSubscribeTrade([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenSubscribeSpreadClick(Sender: TObject);
begin
  KRAKEN.SubscribeSpread([txtKrakenPair.Text]);
end;


procedure TfrmWebSocketClient.btnKrakenFuturesLimitOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPKrakenFuturesOrderSide;
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  if cboKrakenFuturesLimitOrderSide.itemIndex = 0 then
    vSide := kosfBuy
  else
    vSide := kosfSell;

  DoLog(KRAKEN_FUTURES.REST_API.SendLimitOrder(vSide, txtKrakenRESTPair.Text,
    StrToInt(txtKrakenFuturesLimitOrderSize.Text),
    StrToFloat(txtKrakenFuturesLimitOrderPrice.Text, vFS)));
end;


procedure TfrmWebSocketClient.chkKrakenFuturesDemoClick(Sender: TObject);
begin
  KRAKEN_FUTURES.KRAKEN.Demo := chkKrakenFuturesDemo.Checked;
  if chkKrakenFuturesDemo.Checked then
    txtHost.Text := 'demo-futures.kraken.com'
  else
    txtHost.Text := 'futures.kraken.com';
end;


procedure TfrmWebSocketClient.DoBeforeConnectKraken;
begin
  if PageControlKraken.ActivePage = tabKrakenStocks then
  begin
    if KRAKEN.KRAKEN.Beta then
      WSClient.Host := 'beta-ws.kraken.com'
    else if txtKrakenApiKey.Text <> '' then
      WSClient.Host := 'ws-auth.kraken.com';
  end
  else if PageControlKraken.ActivePage = tabKrakenFutures then
  begin
    if KRAKEN_FUTURES.KRAKEN.Demo then
      WSClient.Host := 'demo-futures.kraken.com'
    else
      WSClient.Host := 'futures.kraken.com';
  end;
end;


procedure TfrmWebSocketClient.DoServerKRAKEN;
begin
  DoClear;
  KRAKEN.Client := WSClient;
  KRAKEN.KRAKEN.ApiKey := txtKrakenApiKey.Text;
  KRAKEN.KRAKEN.ApiSecret := txtKrakenApiSecret.Text;

  txtParameters.Text := '/';
  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  chkTLS.Checked := WSClient.TLS;
  chkOverWebSocket.Checked := WSClient.Specifications.RFC6455;
end;


procedure TfrmWebSocketClient.DoServerKRAKENFUT;
begin
  DoClear;
  KRAKEN_FUTURES.Client := WSClient;
  KRAKEN_FUTURES.KRAKEN.ApiKey := txtKrakenApiKey.Text;
  KRAKEN_FUTURES.KRAKEN.ApiSecret := txtKrakenApiSecret.Text;

  txtParameters.Text := '/';
  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
  chkTLS.Checked := WSClient.TLS;
  chkOverWebSocket.Checked := WSClient.Specifications.RFC6455;
end;


procedure TfrmWebSocketClient.FormClose(Sender: TObject;
  var Action: TCloseAction);
begin
  WSClient.Active := False;
end;


procedure TfrmWebSocketClient.KRAKENConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.KRAKENDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.KRAKENKrakenConnect(Sender: TObject;
  ConnectionId, Status, Version: string);
begin
  DoLog('#connected to KRAKEN server');
end;


procedure TfrmWebSocketClient.KRAKENKrakenData(Sender: TObject; aData: string);
begin
  DoLog(aData);
end;


procedure TfrmWebSocketClient.KRAKENKrakenHTTPException(Sender: TObject;
  E: Exception);
begin
  DoLog('#HTTP Exception: ' + E.Message);
end;


procedure TfrmWebSocketClient.KRAKENKrakenSubscribed(Sender: TObject;
  ChannelId: Integer; Pair, Subscription, ChannelName: string; ReqID: Integer);
begin
  DoLog('#subscribed: ' + Subscription + ' ' + Pair + ' ' + ChannelName);
end;


procedure TfrmWebSocketClient.KRAKENKrakenSubscriptionError(Sender: TObject;
  ErrorMessage, Pair, Subscription: string; ReqID: Integer);
begin
  DoLog('#subscription error: ' + ErrorMessage);
end;


procedure TfrmWebSocketClient.KRAKENKrakenSystemStatus(Sender: TObject;
  ConnectionId, Status, Version: string);
begin
  DoLog('#system status: ' + Status);
end;


procedure TfrmWebSocketClient.KRAKENKrakenUnSubscribed(Sender: TObject;
  ChannelId: Integer; Pair, Subscription: string; ReqID: Integer);
begin
  DoLog('#unsubscribed: ' + Subscription + ' ' + Pair);
end;


procedure TfrmWebSocketClient.KRAKEN_FUTURESConnect
  (Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.KRAKEN_FUTURESDisconnect
  (Connection: TsgcWSConnection; Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.KRAKEN_FUTURESKrakenData(Sender: TObject;
  aData: string);
begin
  DoLog(aData);
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


procedure TfrmWebSocketClient.tabKrakenFuturesShow(Sender: TObject);
begin
  txtKrakenPair.Text := 'PI_XBTUSD';
  txtKrakenRESTPair.Text := 'PI_XBTUSD';

  DoServerKRAKENFUT;
end;


procedure TfrmWebSocketClient.tabKRAKENShow(Sender: TObject);
begin
  if PageControlKraken.ActivePage = tabKrakenFutures then
    DoServerKRAKENFUT
  else
    DoServerKRAKEN;
end;


procedure TfrmWebSocketClient.tabKrakenStocksShow(Sender: TObject);
begin
  txtKrakenPair.Text := 'XBT/USD';
  txtKrakenRESTPair.Text := 'XBTUSD';

  DoServerKRAKEN;
end;


procedure TfrmWebSocketClient.txtKrakenApiKeyChange(Sender: TObject);
begin
  KRAKEN.KRAKEN.ApiKey := txtKrakenApiKey.Text;
  KRAKEN_FUTURES.KRAKEN.ApiKey := txtKrakenApiKey.Text;
end;


procedure TfrmWebSocketClient.txtKrakenApiSecretChange(Sender: TObject);
begin
  KRAKEN.KRAKEN.ApiSecret := txtKrakenApiSecret.Text;
  KRAKEN_FUTURES.KRAKEN.ApiSecret := txtKrakenApiSecret.Text;
end;


procedure TfrmWebSocketClient.WSClientConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
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


procedure TfrmWebSocketClient.DoClear;
begin
  KRAKEN.Client := nil;
  KRAKEN_FUTURES.Client := nil;
end;

procedure TfrmWebSocketClient.DoBeforeConnect;
begin
  DoBeforeConnectKraken;
end;

procedure TfrmWebSocketClient.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
end;

end.
```

