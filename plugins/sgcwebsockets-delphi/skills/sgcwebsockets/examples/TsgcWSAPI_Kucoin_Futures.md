# TsgcWSAPI_Kucoin_Futures - Example

Full source of `uKucoin.pas` from the **05.Crypto/11.Kucoin** demo, which uses `TsgcWSAPI_Kucoin_Futures`.

API reference: [TsgcWSAPI_Kucoin_Futures](../reference/api/TsgcWSAPI_Kucoin_Futures.md)
Source demo: `05.Crypto/11.Kucoin` (file `uKucoin.pas`)

```pascal
unit uKucoin;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_Kucoin, sgcHTTP_API_Kucoin;

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
    KUCOIN: TsgcWSAPI_Kucoin;
    KUCOINFUT: TsgcWSAPI_Kucoin_Futures;
    tabKUCOIN: TTabSheet;
    PageControl7: TPageControl;
    tabKucoinStocks: TTabSheet;
    Panel2: TPanel;
    GroupBox7: TGroupBox;
    btnKucoinServiceStatus: TButton;
    btnKucoinServerTime: TButton;
    btnKucoinGetTicker: TButton;
    btnKucoinGet24hrStats: TButton;
    btnKucoinGetRecentOrders: TButton;
    btnKucoinListAccounts: TButton;
    btnKucoinGetAllSubaccounts: TButton;
    btnKucoinListOrders: TButton;
    Panel3: TPanel;
    GroupBox8: TGroupBox;
    btnKucoinSubscribeSymbolSnapshot: TButton;
    btnKucoinUnSubscribeLevel2MarketData: TButton;
    btnKucoinUnSubscribeTradeOrders: TButton;
    btnKucoinUnSubscribeAccountBalance: TButton;
    btnKucoinUnSubscribePositionStatus: TButton;
    btnKucoinSubscribeSymbolTicker: TButton;
    btnKucoinSubscribeLevel2MarketData: TButton;
    btnKucoinSubscribeTradeOrders: TButton;
    btnKucoinSubscribeAccountBalance: TButton;
    btnKucoinSubscribePositionStatus: TButton;
    btnKucoinUnSubscribeSymbolSnapshot: TButton;
    btnKucoinUnSubscribeSymbolTicker: TButton;
    Panel4: TPanel;
    Label101: TLabel;
    Label102: TLabel;
    Label104: TLabel;
    txtKucoinApiKey: TEdit;
    txtKucoinSymbol: TEdit;
    txtKucoinApiSecret: TEdit;
    chkKucoinSandBox: TCheckBox;
    Label105: TLabel;
    txtKucoinApiPassphrase: TEdit;
    Label103: TLabel;
    Label106: TLabel;
    cboKucoinStockMarketOrderSide: TComboBox;
    txtKucoinStockMarketSize: TEdit;
    btnKucoinStockMarketOrder: TButton;
    Label107: TLabel;
    cboKucoinStockLimitOrderSide: TComboBox;
    Label108: TLabel;
    txtKucoinStockLimitSize: TEdit;
    Label109: TLabel;
    txtKucoinStockLimitPrice: TEdit;
    btnKucoinStockLimitOrder: TButton;
    btnKucoinStockCancelAllOrders: TButton;
    btnKucoinSubscribeLevel1: TButton;
    btnKucoinUnSubscribeLevel1: TButton;
    btnKucoinGetDepositAddresses: TButton;
    btnKucoinGetTradeFees: TButton;
    btnKucoinGetPartOrderBook1: TButton;
    tabKucoinFutures: TTabSheet;
    GroupBox9: TGroupBox;
    btnKucoinFutSubscribeSymbolTicker: TButton;
    btnKucoinFutUnSubscribeExecutionData: TButton;
    btnKucoinFutUnSubscribeTradeOrders: TButton;
    btnKucoinFutUnSubscribeAccountBalance: TButton;
    btnKucoinFutUnSubscribePositionChange: TButton;
    btnKucoinFutSubscribeLevel2MarketData: TButton;
    btnKucoinFutSubscribeExecutionData: TButton;
    btnKucoinFutSubscribeTradeOrders: TButton;
    btnKucoinFutSubscribeAccountBalance: TButton;
    btnKucoinFutSubscribePositionChange: TButton;
    btnKucoinFutUnSubscribeSymbolTicker: TButton;
    btnKucoinFutUnSubscribeLevel2MarketData: TButton;
    GroupBox10: TGroupBox;
    Label110: TLabel;
    Label111: TLabel;
    Label112: TLabel;
    Label113: TLabel;
    Label114: TLabel;
    btnKucoinFutServiceStatus: TButton;
    Button62: TButton;
    btnKucoinFutGetOpenContractList: TButton;
    btnKucoinFutGetOrderInfoContract: TButton;
    btnKucoinFutGetTicker: TButton;
    btnKucoinFutGetPartOrderBook20: TButton;
    btnKucoinFutGetTradeHistory: TButton;
    btnKucoinFutGetAccountOverview: TButton;
    btnKucoinFutGetTransactionHistory: TButton;
    cboKucoinFuturesMarketOrderSide: TComboBox;
    txtKucoinFuturesMarketSize: TEdit;
    btnKucoinFuturesLimitOrder: TButton;
    txtKucoinFuturesLimitPrice: TEdit;
    txtKucoinFuturesLimitSize: TEdit;
    cboKucoinFuturesLimitOrderSide: TComboBox;
    btnKucoinFuturesCancelAllOrders: TButton;
    btnKucoinFuturesMarketOrder: TButton;
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnKucoinFutGetAccountOverviewClick(Sender: TObject);
    procedure btnKucoinFutGetOpenContractListClick(Sender: TObject);
    procedure btnKucoinFutGetOrderInfoContractClick(Sender: TObject);
    procedure btnKucoinFutGetPartOrderBook20Click(Sender: TObject);
    procedure btnKucoinFutGetTickerClick(Sender: TObject);
    procedure btnKucoinFutGetTradeHistoryClick(Sender: TObject);
    procedure btnKucoinFutGetTransactionHistoryClick(Sender: TObject);
    procedure btnKucoinFutServiceStatusClick(Sender: TObject);
    procedure btnKucoinFutSubscribeAccountBalanceClick(Sender: TObject);
    procedure btnKucoinFutSubscribeExecutionDataClick(Sender: TObject);
    procedure btnKucoinFutSubscribeLevel2MarketDataClick(Sender: TObject);
    procedure btnKucoinFutSubscribePositionChangeClick(Sender: TObject);
    procedure btnKucoinFutSubscribeSymbolTickerClick(Sender: TObject);
    procedure btnKucoinFutSubscribeTradeOrdersClick(Sender: TObject);
    procedure btnKucoinFutUnSubscribeAccountBalanceClick(Sender: TObject);
    procedure btnKucoinFutUnSubscribeExecutionDataClick(Sender: TObject);
    procedure btnKucoinFutUnSubscribeLevel2MarketDataClick(Sender: TObject);
    procedure btnKucoinFutUnSubscribePositionChangeClick(Sender: TObject);
    procedure btnKucoinFutUnSubscribeSymbolTickerClick(Sender: TObject);
    procedure btnKucoinFutUnSubscribeTradeOrdersClick(Sender: TObject);
    procedure btnKucoinFuturesCancelAllOrdersClick(Sender: TObject);
    procedure btnKucoinFuturesLimitOrderClick(Sender: TObject);
    procedure btnKucoinFuturesMarketOrderClick(Sender: TObject);
    procedure btnKucoinSubscribeLevel1Click(Sender: TObject);
    procedure btnKucoinUnSubscribeLevel1Click(Sender: TObject);
    procedure btnKucoinGetDepositAddressesClick(Sender: TObject);
    procedure btnKucoinGetTradeFeesClick(Sender: TObject);
    procedure btnKucoinGetPartOrderBook1Click(Sender: TObject);
    procedure btnKucoinGet24hrStatsClick(Sender: TObject);
    procedure btnKucoinGetAllSubaccountsClick(Sender: TObject);
    procedure btnKucoinGetRecentOrdersClick(Sender: TObject);
    procedure btnKucoinGetTickerClick(Sender: TObject);
    procedure btnKucoinListAccountsClick(Sender: TObject);
    procedure btnKucoinListOrdersClick(Sender: TObject);
    procedure btnKucoinServerTimeClick(Sender: TObject);
    procedure btnKucoinServiceStatusClick(Sender: TObject);
    procedure btnKucoinStockCancelAllOrdersClick(Sender: TObject);
    procedure btnKucoinStockLimitOrderClick(Sender: TObject);
    procedure btnKucoinStockMarketOrderClick(Sender: TObject);
    procedure btnKucoinSubscribeAccountBalanceClick(Sender: TObject);
    procedure btnKucoinSubscribeLevel2MarketDataClick(Sender: TObject);
    procedure btnKucoinSubscribePositionStatusClick(Sender: TObject);
    procedure btnKucoinSubscribeSymbolSnapshotClick(Sender: TObject);
    procedure btnKucoinSubscribeSymbolTickerClick(Sender: TObject);
    procedure btnKucoinSubscribeTradeOrdersClick(Sender: TObject);
    procedure btnKucoinUnSubscribeAccountBalanceClick(Sender: TObject);
    procedure btnKucoinUnSubscribeLevel2MarketDataClick(Sender: TObject);
    procedure btnKucoinUnSubscribePositionStatusClick(Sender: TObject);
    procedure btnKucoinUnSubscribeSymbolSnapshotClick(Sender: TObject);
    procedure btnKucoinUnSubscribeSymbolTickerClick(Sender: TObject);
    procedure btnKucoinUnSubscribeTradeOrdersClick(Sender: TObject);
    procedure Button62Click(Sender: TObject);
    procedure chkKucoinSandBoxClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure tabKucoinFuturesShow(Sender: TObject);
    procedure tabKUCOINShow(Sender: TObject);
    procedure tabKucoinStocksShow(Sender: TObject);
    procedure txtKucoinApiKeyChange(Sender: TObject);
    procedure txtKucoinApiPassphraseChange(Sender: TObject);
    procedure txtKucoinApiSecretChange(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServerKUCOIN;
    procedure DoServerKUCOINFUT;
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


procedure TfrmWebSocketClient.btnKucoinFutGetAccountOverviewClick
  (Sender: TObject);
begin
  DoLog(KUCOINFUT.REST_API.GetAccountOverview);
end;


procedure TfrmWebSocketClient.btnKucoinFutGetOpenContractListClick
  (Sender: TObject);
begin
  DoLog(KUCOINFUT.REST_API.GetOpenContractList);
end;


procedure TfrmWebSocketClient.btnKucoinFutGetOrderInfoContractClick
  (Sender: TObject);
begin
  DoLog(KUCOINFUT.REST_API.GetOrderInfoContract(txtKucoinSymbol.Text));
end;


procedure TfrmWebSocketClient.btnKucoinFutGetPartOrderBook20Click
  (Sender: TObject);
begin
  DoLog(KUCOINFUT.REST_API.GetPartOrderBook20(txtKucoinSymbol.Text));
end;


procedure TfrmWebSocketClient.btnKucoinFutGetTickerClick(Sender: TObject);
begin
  DoLog(KUCOINFUT.REST_API.GetTicker(txtKucoinSymbol.Text));
end;


procedure TfrmWebSocketClient.btnKucoinFutGetTradeHistoryClick(Sender: TObject);
begin
  DoLog(KUCOINFUT.REST_API.GetTradeHistory(txtKucoinSymbol.Text));
end;


procedure TfrmWebSocketClient.btnKucoinFutGetTransactionHistoryClick
  (Sender: TObject);
begin
  DoLog(KUCOINFUT.REST_API.GetTransactionHistory);
end;


procedure TfrmWebSocketClient.btnKucoinFutServiceStatusClick(Sender: TObject);
begin
  DoLog(KUCOINFUT.REST_API.GetServiceStatus);
end;


procedure TfrmWebSocketClient.btnKucoinFutSubscribeAccountBalanceClick
  (Sender: TObject);
begin
  KUCOINFUT.SubscribeAccountBalance(True);
end;


procedure TfrmWebSocketClient.btnKucoinFutSubscribeExecutionDataClick
  (Sender: TObject);
begin
  KUCOINFUT.SubscribeExecutionData(txtKucoinSymbol.Text);
end;


procedure TfrmWebSocketClient.btnKucoinFutSubscribeLevel2MarketDataClick
  (Sender: TObject);
begin
  KUCOINFUT.SubscribeLevel2MarketData(txtKucoinSymbol.Text);
end;


procedure TfrmWebSocketClient.btnKucoinFutSubscribePositionChangeClick
  (Sender: TObject);
begin
  KUCOINFUT.SubscribePositionChange(txtKucoinSymbol.Text, True);
end;


procedure TfrmWebSocketClient.btnKucoinFutSubscribeSymbolTickerClick
  (Sender: TObject);
begin
  KUCOINFUT.SubscribeSymbolTickerV2(txtKucoinSymbol.Text);
end;


procedure TfrmWebSocketClient.btnKucoinFutSubscribeTradeOrdersClick
  (Sender: TObject);
begin
  KUCOINFUT.SubscribeTradeOrders(True);
end;


procedure TfrmWebSocketClient.btnKucoinFutUnSubscribeAccountBalanceClick
  (Sender: TObject);
begin
  KUCOINFUT.UnSubscribeAccountBalance(True);
end;


procedure TfrmWebSocketClient.btnKucoinFutUnSubscribeExecutionDataClick
  (Sender: TObject);
begin
  KUCOINFUT.UnSubscribeExecutionData(txtKucoinSymbol.Text);
end;


procedure TfrmWebSocketClient.btnKucoinFutUnSubscribeLevel2MarketDataClick
  (Sender: TObject);
begin
  KUCOINFUT.UnSubscribeLevel2MarketData(txtKucoinSymbol.Text);
end;


procedure TfrmWebSocketClient.btnKucoinFutUnSubscribePositionChangeClick
  (Sender: TObject);
begin
  KUCOINFUT.UnSubscribePositionChange(txtKucoinSymbol.Text, True);
end;


procedure TfrmWebSocketClient.btnKucoinFutUnSubscribeSymbolTickerClick
  (Sender: TObject);
begin
  KUCOINFUT.UnSubscribeSymbolTickerV2(txtKucoinSymbol.Text);
end;


procedure TfrmWebSocketClient.btnKucoinFutUnSubscribeTradeOrdersClick
  (Sender: TObject);
begin
  KUCOINFUT.UnSubscribeTradeOrders(True);
end;


procedure TfrmWebSocketClient.btnKucoinFuturesCancelAllOrdersClick
  (Sender: TObject);
begin
  DoLog(KUCOINFUT.REST_API.StopOrderMassCancellation(txtKucoinSymbol.Text));
  DoLog(KUCOINFUT.REST_API.LimitOrderMassCancellation(txtKucoinSymbol.Text));
end;


procedure TfrmWebSocketClient.btnKucoinFuturesLimitOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPKucoinOrderSide;
begin
  if cboKucoinFuturesMarketOrderSide.itemIndex = 0 then
    vSide := kosBuy
  else
    vSide := kosSell;

  DoLog(KUCOINFUT.REST_API.PlaceMarketOrder(vSide, txtKucoinSymbol.Text,
    StrToInt(txtKucoinFuturesMarketSize.Text)));
end;


procedure TfrmWebSocketClient.btnKucoinFuturesMarketOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPKucoinOrderSide;
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  if cboKucoinFuturesLimitOrderSide.itemIndex = 0 then
    vSide := kosBuy
  else
    vSide := kosSell;

  DoLog(KUCOINFUT.REST_API.PlaceLimitOrder(vSide, txtKucoinSymbol.Text,
    StrToInt(txtKucoinFuturesLimitSize.Text),
    StrToFloat(txtKucoinFuturesLimitPrice.Text, vFS)));
end;


procedure TfrmWebSocketClient.btnKucoinSubscribeLevel1Click(Sender: TObject);
begin
  KUCOIN.SubscribeLevel1(txtKucoinSymbol.Text);
end;


procedure TfrmWebSocketClient.btnKucoinUnSubscribeLevel1Click(Sender: TObject);
begin
  KUCOIN.UnSubscribeLevel1(txtKucoinSymbol.Text);
end;


procedure TfrmWebSocketClient.btnKucoinGetDepositAddressesClick(
  Sender: TObject);
begin
  DoLog(KUCOIN.REST_API.GetDepositAddresses(txtKucoinSymbol.Text));
end;


procedure TfrmWebSocketClient.btnKucoinGetTradeFeesClick(Sender: TObject);
begin
  DoLog(KUCOIN.REST_API.GetTradeFees(txtKucoinSymbol.Text));
end;


procedure TfrmWebSocketClient.btnKucoinGetPartOrderBook1Click(
  Sender: TObject);
begin
  DoLog(KUCOIN.REST_API.GetPartOrderBook1(txtKucoinSymbol.Text));
end;


procedure TfrmWebSocketClient.btnKucoinGet24hrStatsClick(Sender: TObject);
begin
  DoLog(KUCOIN.REST_API.Get24hrStats(txtKucoinSymbol.Text));
end;


procedure TfrmWebSocketClient.btnKucoinGetAllSubaccountsClick(Sender: TObject);
begin
  DoLog(KUCOIN.REST_API.GetAllSubAccounts);
end;


procedure TfrmWebSocketClient.btnKucoinGetRecentOrdersClick(Sender: TObject);
begin
  DoLog(KUCOIN.REST_API.GetRecentOrders);
end;


procedure TfrmWebSocketClient.btnKucoinGetTickerClick(Sender: TObject);
begin
  DoLog(KUCOIN.REST_API.GetTicker(txtKucoinSymbol.Text));
end;


procedure TfrmWebSocketClient.btnKucoinListAccountsClick(Sender: TObject);
begin
  DoLog(KUCOIN.REST_API.GetListAccounts);
end;


procedure TfrmWebSocketClient.btnKucoinListOrdersClick(Sender: TObject);
begin
  DoLog(KUCOIN.REST_API.ListOrders());
end;


procedure TfrmWebSocketClient.btnKucoinServerTimeClick(Sender: TObject);
begin
  DoLog(KUCOIN.REST_API.GetServerTime);
end;


procedure TfrmWebSocketClient.btnKucoinServiceStatusClick(Sender: TObject);
begin
  DoLog(KUCOIN.REST_API.GetServiceStatus);
end;


procedure TfrmWebSocketClient.btnKucoinStockCancelAllOrdersClick
  (Sender: TObject);
begin
  DoLog(KUCOIN.REST_API.CancelAllOrders(txtKucoinSymbol.Text));
end;


procedure TfrmWebSocketClient.btnKucoinStockLimitOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPKucoinOrderSide;
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  if cboKucoinStockLimitOrderSide.itemIndex = 0 then
    vSide := kosBuy
  else
    vSide := kosSell;

  DoLog(KUCOIN.REST_API.PlaceLimitOrder(vSide, txtKucoinSymbol.Text,
    StrToFloat(txtKucoinStockLimitSize.Text, vFS),
    StrToFloat(txtKucoinStockLimitPrice.Text, vFS)));
end;


procedure TfrmWebSocketClient.btnKucoinStockMarketOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPKucoinOrderSide;
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  if cboKucoinStockMarketOrderSide.itemIndex = 0 then
    vSide := kosBuy
  else
    vSide := kosSell;

  DoLog(KUCOIN.REST_API.PlaceMarketOrder(vSide, txtKucoinSymbol.Text,
    StrToFloat(txtKucoinStockMarketSize.Text, vFS)));
end;


procedure TfrmWebSocketClient.btnKucoinSubscribeAccountBalanceClick
  (Sender: TObject);
begin
  KUCOIN.SubscribeAccountBalance(True);
end;


procedure TfrmWebSocketClient.btnKucoinSubscribeLevel2MarketDataClick
  (Sender: TObject);
begin
  KUCOIN.SubscribeLevel2MarketData(txtKucoinSymbol.Text);
end;


procedure TfrmWebSocketClient.btnKucoinSubscribePositionStatusClick
  (Sender: TObject);
begin
  KUCOIN.SubscribePositionStatus(True);
end;


procedure TfrmWebSocketClient.btnKucoinSubscribeSymbolSnapshotClick
  (Sender: TObject);
begin
  KUCOIN.SubscribeSymbolSnapshot(txtKucoinSymbol.Text);
end;


procedure TfrmWebSocketClient.btnKucoinSubscribeSymbolTickerClick
  (Sender: TObject);
begin
  KUCOIN.SubscribeSymbolTicker(txtKucoinSymbol.Text);
end;


procedure TfrmWebSocketClient.btnKucoinSubscribeTradeOrdersClick
  (Sender: TObject);
begin
  KUCOIN.SubscribeTradeOrders(True);
end;


procedure TfrmWebSocketClient.btnKucoinUnSubscribeAccountBalanceClick
  (Sender: TObject);
begin
  KUCOIN.UnSubscribeAccountBalance(True);
end;


procedure TfrmWebSocketClient.btnKucoinUnSubscribeLevel2MarketDataClick
  (Sender: TObject);
begin
  KUCOIN.UnSubscribeLevel2MarketData(txtKucoinSymbol.Text);
end;


procedure TfrmWebSocketClient.btnKucoinUnSubscribePositionStatusClick
  (Sender: TObject);
begin
  KUCOIN.UnSubscribePositionStatus(True);
end;


procedure TfrmWebSocketClient.btnKucoinUnSubscribeSymbolSnapshotClick
  (Sender: TObject);
begin
  KUCOIN.UnSubscribeSymbolSnapshot(txtKucoinSymbol.Text);
end;


procedure TfrmWebSocketClient.btnKucoinUnSubscribeSymbolTickerClick
  (Sender: TObject);
begin
  KUCOIN.UnSubscribeSymbolTicker(txtKucoinSymbol.Text);
end;


procedure TfrmWebSocketClient.btnKucoinUnSubscribeTradeOrdersClick
  (Sender: TObject);
begin
  KUCOIN.UnSubscribeTradeOrders(True);
end;


procedure TfrmWebSocketClient.Button62Click(Sender: TObject);
begin
  DoLog(KUCOINFUT.REST_API.GetServerTime);
end;


procedure TfrmWebSocketClient.chkKucoinSandBoxClick(Sender: TObject);
begin
  KUCOIN.Kucoin.SandBox := chkKucoinSandBox.Checked;
  KUCOINFUT.Kucoin.SandBox := chkKucoinSandBox.Checked;

  tabKUCOINShow(nil);
end;


procedure TfrmWebSocketClient.DoServerKUCOIN;
begin
  DoClear;
  KUCOIN.Client := WSClient;

  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
  chkTLS.Checked := WSClient.TLS;
  chkOverWebSocket.Checked := WSClient.Specifications.RFC6455;

  txtKucoinSymbol.Text := 'BTC-USDT';
end;


procedure TfrmWebSocketClient.DoServerKUCOINFUT;
begin
  DoClear;
  KUCOINFUT.Client := WSClient;

  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
  chkTLS.Checked := WSClient.TLS;
  chkOverWebSocket.Checked := WSClient.Specifications.RFC6455;

  txtKucoinSymbol.Text := 'XBTUSDTM';
end;


procedure TfrmWebSocketClient.FormClose(Sender: TObject;
  var Action: TCloseAction);
begin
  WSClient.Active := False;
end;


procedure TfrmWebSocketClient.tabKucoinFuturesShow(Sender: TObject);
begin
  DoServerKUCOINFUT;
end;


procedure TfrmWebSocketClient.tabKUCOINShow(Sender: TObject);
begin
  if PageControl7.ActivePage = tabKucoinFutures then
    DoServerKUCOINFUT
  else
    DoServerKUCOIN;
end;


procedure TfrmWebSocketClient.tabKucoinStocksShow(Sender: TObject);
begin
  DoServerKUCOIN;
end;


procedure TfrmWebSocketClient.txtKucoinApiKeyChange(Sender: TObject);
begin
  KUCOIN.Kucoin.ApiKey := txtKucoinApiKey.Text;
  KUCOINFUT.Kucoin.ApiKey := txtKucoinApiKey.Text;
end;


procedure TfrmWebSocketClient.txtKucoinApiPassphraseChange(Sender: TObject);
begin
  KUCOIN.Kucoin.ApiPassphrase := txtKucoinApiPassphrase.Text;
  KUCOINFUT.Kucoin.ApiPassphrase := txtKucoinApiPassphrase.Text;
end;


procedure TfrmWebSocketClient.txtKucoinApiSecretChange(Sender: TObject);
begin
  KUCOIN.Kucoin.ApiSecret := txtKucoinApiSecret.Text;
  KUCOINFUT.Kucoin.ApiSecret := txtKucoinApiSecret.Text;
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
  KUCOIN.Client := nil;
  KUCOINFUT.Client := nil;
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

