# TsgcWSAPI_Bitstamp - Example

Full source of `uBitstamp.pas` from the **05.Crypto/02.Bitstamp** demo, which uses `TsgcWSAPI_Bitstamp`.

API reference: [TsgcWSAPI_Bitstamp](../reference/api/TsgcWSAPI_Bitstamp.md)
Source demo: `05.Crypto/02.Bitstamp` (file `uBitstamp.pas`)

```pascal
unit uBitstamp;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_Bitstamp;

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
    BITSTAMP: TsgcWSAPI_Bitstamp;
    tabBITSTAMP: TTabSheet;
    pageBitstamp: TPageControl;
    tabBitstampWebSocket: TTabSheet;
    btnTickerBITSTAMP: TButton;
    btnLiveOrdersBITSTAMP: TButton;
    btnOrderBookBITSTAMP: TButton;
    btnDetailOrderBookBITSTAMP: TButton;
    btnFullOrderBookBITSTAMP: TButton;
    tabBitstampRESTPublic: TTabSheet;
    pnlBitstampTop: TPanel;
    txtBitstampCurrency: TEdit;
    Label69: TLabel;
    txtBistampAPI: TEdit;
    Label70: TLabel;
    btnBitstampCurrencies: TButton;
    btnBitstampCurrencyPairTicker: TButton;
    btnBitstampOrderBook: TButton;
    btnBitstampEURUSD: TButton;
    tabBitstampRESTPrivate: TTabSheet;
    btnBitstampAccountBalances: TButton;
    Label71: TLabel;
    txtBitstampSecret: TEdit;
    Label72: TLabel;
    Label73: TLabel;
    txtBitstampMarketAmount: TEdit;
    cboBitstampMarketSide: TComboBox;
    btnBitstampMarketOrder: TButton;
    txtBitstampLimitAmount: TEdit;
    cboBitstampLimitSide: TComboBox;
    Label74: TLabel;
    Label76: TLabel;
    Label77: TLabel;
    txtBitstampLimitPrice: TEdit;
    btnBitstampLimitOrder: TButton;
    btnBitstampAllOpenOrders: TButton;
    btnBitstampCancelAllOrders: TButton;
    btnBitstampPrivateOrders: TButton;
    btnBitstampPrivateTrades: TButton;
    tabBitstampRESTNew: TTabSheet;
    btnBitstampUserTransactions: TButton;
    btnBitstampTradingFees: TButton;
    btnBitstampWithdrawalFees: TButton;
    btnBitstampDepositAddress: TButton;
    btnBitstampEarnSubscriptions: TButton;
    btnBitstampEarnTransactions: TButton;
    btnBitstampTravelRuleVASPs: TButton;
    btnBitstampMarkets: TButton;
    procedure BITSTAMPConnect(Connection: TsgcWSConnection);
    procedure BITSTAMPDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure BITSTAMPMessage(Connection: TsgcWSConnection; const Text: string);
    procedure BITSTAMPPusherConnect(Sender: TObject; Socket_id: string;
      Timeout: Integer);
    procedure BITSTAMPPusherError(Sender: TObject; Code: Integer; Msg: string);
    procedure BITSTAMPPusherEvent(Sender: TObject;
      Event, Channel, Data: string);
    procedure BITSTAMPPusherSubscribe(Sender: TObject; Channel, Data: string);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnFullOrderBookBITSTAMPClick(Sender: TObject);
    procedure btnLiveOrdersBITSTAMPClick(Sender: TObject);
    procedure btnOrderBookBITSTAMPClick(Sender: TObject);
    procedure btnTickerBITSTAMPClick(Sender: TObject);
    procedure btnDetailOrderBookBITSTAMPClick(Sender: TObject);
    procedure btnBitstampAccountBalancesClick(Sender: TObject);
    procedure btnBitstampAllOpenOrdersClick(Sender: TObject);
    procedure btnBitstampCancelAllOrdersClick(Sender: TObject);
    procedure btnBitstampCurrenciesClick(Sender: TObject);
    procedure btnBitstampCurrencyPairTickerClick(Sender: TObject);
    procedure btnBitstampEURUSDClick(Sender: TObject);
    procedure btnBitstampLimitOrderClick(Sender: TObject);
    procedure btnBitstampMarketOrderClick(Sender: TObject);
    procedure btnBitstampOrderBookClick(Sender: TObject);
    procedure btnBitstampPrivateOrdersClick(Sender: TObject);
    procedure btnBitstampPrivateTradesClick(Sender: TObject);
    procedure btnBitstampUserTransactionsClick(Sender: TObject);
    procedure btnBitstampTradingFeesClick(Sender: TObject);
    procedure btnBitstampWithdrawalFeesClick(Sender: TObject);
    procedure btnBitstampDepositAddressClick(Sender: TObject);
    procedure btnBitstampEarnSubscriptionsClick(Sender: TObject);
    procedure btnBitstampEarnTransactionsClick(Sender: TObject);
    procedure btnBitstampTravelRuleVASPsClick(Sender: TObject);
    procedure btnBitstampMarketsClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure tabBITSTAMPShow(Sender: TObject);
    procedure txtBistampAPIChange(Sender: TObject);
    procedure txtBitstampSecretChange(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServerBITSTAMP;
  end;

var
  frmWebSocketClient: TfrmWebSocketClient;

implementation

uses
  sgcWebSocket_Helpers, sgcJSON, StrUtils, sgcBase_Helpers,
  ShellAPI, DateUtils;
{$R *.dfm}

procedure TfrmWebSocketClient.BITSTAMPConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.BITSTAMPDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.BITSTAMPMessage(Connection: TsgcWSConnection;
  const Text: string);
begin
  DoLog(Text);
end;


procedure TfrmWebSocketClient.BITSTAMPPusherConnect(Sender: TObject;
  Socket_id: string; Timeout: Integer);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.BITSTAMPPusherError(Sender: TObject;
  Code: Integer; Msg: string);
begin
  DoLog('#error: ' + Msg);
end;


procedure TfrmWebSocketClient.BITSTAMPPusherEvent(Sender: TObject;
  Event, Channel, Data: string);
begin
  DoLog('Event: ' + Event + ' Channel: ' + Channel + ' ' + Data);
end;


procedure TfrmWebSocketClient.BITSTAMPPusherSubscribe(Sender: TObject;
  Channel, Data: string);
begin
  DoLog('#subscribed: ' + Channel);
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


procedure TfrmWebSocketClient.btnFullOrderBookBITSTAMPClick(Sender: TObject);
begin
  BITSTAMP.SubscribeLiveFullOrderBook(txtBitstampCurrency.Text);
end;


procedure TfrmWebSocketClient.btnLiveOrdersBITSTAMPClick(Sender: TObject);
begin
  BITSTAMP.SubscribeLiveOrders(txtBitstampCurrency.Text);
end;


procedure TfrmWebSocketClient.btnOrderBookBITSTAMPClick(Sender: TObject);
begin
  BITSTAMP.SubscribeLiveOrderBook(txtBitstampCurrency.Text);
end;


procedure TfrmWebSocketClient.btnTickerBITSTAMPClick(Sender: TObject);
begin
  BITSTAMP.SubscribeLiveTicker(txtBitstampCurrency.Text);
end;


procedure TfrmWebSocketClient.btnDetailOrderBookBITSTAMPClick(Sender: TObject);
begin
  BITSTAMP.SubscribeLiveDetailOrderBook(txtBitstampCurrency.Text);
end;


procedure TfrmWebSocketClient.btnBitstampAccountBalancesClick(Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.GetAccountBalances);
end;


procedure TfrmWebSocketClient.btnBitstampAllOpenOrdersClick(Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.GetAllOpenOrders);
end;


procedure TfrmWebSocketClient.btnBitstampCancelAllOrdersClick(Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.CancelAllOrders);
end;


procedure TfrmWebSocketClient.btnBitstampCurrenciesClick(Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.GetCurrencies);
end;


procedure TfrmWebSocketClient.btnBitstampCurrencyPairTickerClick
  (Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.GetCurrencyPairTicker(txtBitstampCurrency.Text));
end;


procedure TfrmWebSocketClient.btnBitstampEURUSDClick(Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.GetEURUSDConversionRate);
end;


procedure TfrmWebSocketClient.btnBitstampLimitOrderClick(Sender: TObject);
begin
  if cboBitstampLimitSide.itemIndex = 0 then
    DoLog(BITSTAMP.REST_API.BuyLimitOrder(txtBitstampCurrency.Text,
      txtBitstampLimitAmount.Text, txtBitstampLimitPrice.Text))
  else
    DoLog(BITSTAMP.REST_API.SellLimitOrder(txtBitstampCurrency.Text,
      txtBitstampLimitAmount.Text, txtBitstampLimitPrice.Text));
end;


procedure TfrmWebSocketClient.btnBitstampMarketOrderClick(Sender: TObject);
begin
  if cboBitstampMarketSide.itemIndex = 0 then
    DoLog(BITSTAMP.REST_API.BuyMarketOrder(txtBitstampCurrency.Text,
      txtBitstampMarketAmount.Text))
  else
    DoLog(BITSTAMP.REST_API.SellMarketOrder(txtBitstampCurrency.Text,
      txtBitstampMarketAmount.Text));
end;


procedure TfrmWebSocketClient.btnBitstampOrderBookClick(Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.GetOrderBook(txtBitstampCurrency.Text));
end;


procedure TfrmWebSocketClient.btnBitstampPrivateOrdersClick(Sender: TObject);
begin
  BITSTAMP.SubscribeMyOrders(txtBitstampCurrency.Text);
end;


procedure TfrmWebSocketClient.btnBitstampPrivateTradesClick(Sender: TObject);
begin
  BITSTAMP.SubscribeMyTrades(txtBitstampCurrency.Text);
end;


procedure TfrmWebSocketClient.btnBitstampUserTransactionsClick(Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.GetUserTransactions);
end;


procedure TfrmWebSocketClient.btnBitstampTradingFeesClick(Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.GetTradingFees);
end;


procedure TfrmWebSocketClient.btnBitstampWithdrawalFeesClick(Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.GetWithdrawalFees);
end;


procedure TfrmWebSocketClient.btnBitstampDepositAddressClick(Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.GetCryptoDepositAddress('btc'));
end;


procedure TfrmWebSocketClient.btnBitstampEarnSubscriptionsClick(Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.GetEarnSubscriptions);
end;


procedure TfrmWebSocketClient.btnBitstampEarnTransactionsClick(Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.GetEarnTransactions);
end;


procedure TfrmWebSocketClient.btnBitstampTravelRuleVASPsClick(Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.GetTravelRuleVASPs);
end;


procedure TfrmWebSocketClient.btnBitstampMarketsClick(Sender: TObject);
begin
  DoLog(BITSTAMP.REST_API.GetMarkets);
end;


procedure TfrmWebSocketClient.DoServerBITSTAMP;
begin
  DoClear;
  BITSTAMP.Client := WSClient;

  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
  chkTLS.Checked := WSClient.TLS;
  chkOverWebSocket.Checked := True;
end;


procedure TfrmWebSocketClient.FormClose(Sender: TObject;
  var Action: TCloseAction);
begin
  WSClient.Active := False;
end;


procedure TfrmWebSocketClient.tabBITSTAMPShow(Sender: TObject);
begin
  DoServerBITSTAMP;
end;


procedure TfrmWebSocketClient.txtBistampAPIChange(Sender: TObject);
begin
  BITSTAMP.Bitstamp.ApiKey := txtBistampAPI.Text;
end;


procedure TfrmWebSocketClient.txtBitstampSecretChange(Sender: TObject);
begin
  BITSTAMP.Bitstamp.ApiSecret := txtBitstampSecret.Text;
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
  BITSTAMP.Client := nil;
end;

procedure TfrmWebSocketClient.DoBeforeConnect;
begin
end;

procedure TfrmWebSocketClient.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
end;

end.
```

