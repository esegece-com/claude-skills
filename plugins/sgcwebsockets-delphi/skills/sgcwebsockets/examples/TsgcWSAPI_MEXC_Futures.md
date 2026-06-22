# TsgcWSAPI_MEXC_Futures - Example

Full source of `uMEXC.pas` from the **05.Crypto/15.MEXC** demo, which uses `TsgcWSAPI_MEXC_Futures`.

API reference: [TsgcWSAPI_MEXC_Futures](../reference/api/TsgcWSAPI_MEXC_Futures.md)
Source demo: `05.Crypto/15.MEXC` (file `uMEXC.pas`)

```pascal
unit uMEXC;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_MEXC, sgcWebSocket_API_MEXC_Proto,
  sgcHTTP_API_MEXC;

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
    tabMEXC: TTabSheet;
    Label19: TLabel;
    txtMEXCApiKey: TEdit;
    Label20: TLabel;
    txtMEXCApiSecret: TEdit;
    Label21: TLabel;
    txtMEXCSymbol: TEdit;
    PageControl3: TPageControl;
    tabMEXC_WebSocketFutures: TTabSheet;
    btnMEXCFUT_SubscribeTicker: TButton;
    btnMEXCFUT_SubscribeKLine: TButton;
    btnMEXCFUT_SubscribeDepth: TButton;
    btnMEXCFUT_UnSubscribeTicker: TButton;
    btnMEXCFUT_UnSubscribeKLine: TButton;
    btnMEXCFUT_UnSubscribeDepth: TButton;
    MEXCFUT: TsgcWSAPI_MEXC_Futures;
    MEXC: TsgcWSAPI_MEXC;
    tabMEXC_WebSocket: TTabSheet;
    btnMEXC_SubscribeTrade: TButton;
    btnMEXC_UnSubscribeTrade: TButton;
    btnMEXC_SubscribeKLine: TButton;
    btnMEXC_UnSubscribeKLine: TButton;
    btnMEXC_SubscribeAccountUpdate: TButton;
    btnMEXC_UnSubscribeAccountUpdate: TButton;
    btnMEXC_SubscribeAccountDeals: TButton;
    btnMEXC_UnSubscribeAccountDeals: TButton;
    btnMEXC_SubscribeAccountOrders: TButton;
    btnMEXC_UnSubscribeAccountOrders: TButton;
    chkMEXC_UserStream: TCheckBox;
    tabMEXC_RESTSpot: TTabSheet;
    tabMEXC_RESTFutures: TTabSheet;
    btnMEXCSpotExchangeInformation: TButton;
    btnMEXCSpotOrderBook: TButton;
    btnMEXCSpotTrades: TButton;
    btnMEXCSpotKlines: TButton;
    btnMEXCSpotAccountInformation: TButton;
    btnMEXCSpotOpenOrders: TButton;
    btnMEXCFuturesDepth: TButton;
    btnMEXCFuturesDeals: TButton;
    btnMEXCFuturesKlines: TButton;
    btnMEXCFuturesIndexPrice: TButton;
    btnMEXCFuturesAccountAssets: TButton;
    btnMEXCFuturesPositionList: TButton;
    btnMEXCGetTradeFee: TButton;
    btnMEXCGetDepositHistory: TButton;
    btnMEXCGetAllTickers: TButton;
    btnMEXCGetOpenPositions: TButton;
    btnMEXCSubscribePersonalOrder: TButton;
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnMEXCFUT_SubscribeDepthClick(Sender: TObject);
    procedure btnMEXCFUT_SubscribeKLineClick(Sender: TObject);
    procedure btnMEXCFUT_SubscribeTickerClick(Sender: TObject);
    procedure btnMEXCFUT_UnSubscribeDepthClick(Sender: TObject);
    procedure btnMEXCFUT_UnSubscribeKLineClick(Sender: TObject);
    procedure btnMEXCFUT_UnSubscribeTickerClick(Sender: TObject);
    procedure btnMEXC_SubscribeAccountDealsClick(Sender: TObject);
    procedure btnMEXC_SubscribeAccountOrdersClick(Sender: TObject);
    procedure btnMEXC_SubscribeAccountUpdateClick(Sender: TObject);
    procedure btnMEXC_SubscribeKLineClick(Sender: TObject);
    procedure btnMEXC_SubscribeTradeClick(Sender: TObject);
    procedure btnMEXC_UnSubscribeAccountDealsClick(Sender: TObject);
    procedure btnMEXC_UnSubscribeAccountOrdersClick(Sender: TObject);
    procedure btnMEXC_UnSubscribeAccountUpdateClick(Sender: TObject);
    procedure btnMEXC_UnSubscribeKLineClick(Sender: TObject);
    procedure btnMEXC_UnSubscribeTradeClick(Sender: TObject);
    procedure btnMEXCSpotExchangeInformationClick(Sender: TObject);
    procedure btnMEXCSpotOrderBookClick(Sender: TObject);
    procedure btnMEXCSpotTradesClick(Sender: TObject);
    procedure btnMEXCSpotKlinesClick(Sender: TObject);
    procedure btnMEXCSpotAccountInformationClick(Sender: TObject);
    procedure btnMEXCSpotOpenOrdersClick(Sender: TObject);
    procedure btnMEXCFuturesDepthClick(Sender: TObject);
    procedure btnMEXCFuturesDealsClick(Sender: TObject);
    procedure btnMEXCFuturesKlinesClick(Sender: TObject);
    procedure btnMEXCFuturesIndexPriceClick(Sender: TObject);
    procedure btnMEXCFuturesAccountAssetsClick(Sender: TObject);
    procedure btnMEXCFuturesPositionListClick(Sender: TObject);
    procedure btnMEXCGetTradeFeeClick(Sender: TObject);
    procedure btnMEXCGetDepositHistoryClick(Sender: TObject);
    procedure btnMEXCGetAllTickersClick(Sender: TObject);
    procedure btnMEXCGetOpenPositionsClick(Sender: TObject);
    procedure btnMEXCSubscribePersonalOrderClick(Sender: TObject);
    procedure chkMEXC_UserStreamClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure MEXCConnect(Connection: TsgcWSConnection);
    procedure MEXCDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure MEXCFUTConnect(Connection: TsgcWSConnection);
    procedure MEXCFUTDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure MEXCFUTMEXCError(Sender: TObject; const aData, aRawMessage: string);
    procedure MEXCFUTMEXCLogin(Sender: TObject; const aRawMessage: string);
    procedure MEXCFUTMEXCMessage(Sender: TObject; const aChannel, aRawMessage:
        string);
    procedure MEXCFUTMEXCSubscribed(Sender: TObject; const aChannel, aRawMessage:
        string);
    procedure MEXCFUTMEXCUnsubscribed(Sender: TObject; const aChannel,
        aRawMessage: string);
    procedure MEXCMEXCException(Sender: TObject; const E: Exception);
    procedure MEXCMEXCMarketStream(Sender: TObject; const aMessage:
        TsgcMEXCSpotProtoMessage; const aStream: TMemoryStream);
    procedure MEXCMEXCResponse(Sender: TObject; const aId, aCode: Int64; const
        aMessage: string);
    procedure MEXCMEXCUserDataStream(Sender: TObject; const aChannel, aRawMessage:
        string);
    procedure tabMEXCShow(Sender: TObject);
    procedure tabMEXC_RESTFuturesShow(Sender: TObject);
    procedure tabMEXC_RESTSpotShow(Sender: TObject);
    procedure tabMEXC_WebSocketFuturesShow(Sender: TObject);
    procedure tabMEXC_WebSocketShow(Sender: TObject);
    procedure txtMEXCApiKeyChange(Sender: TObject);
    procedure txtMEXCApiSecretChange(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServerMEXC;
    procedure DoServerMEXCFUT;
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


procedure TfrmWebSocketClient.btnMEXCFUT_SubscribeDepthClick(Sender: TObject);
begin
  MEXCFUT.SubscribeDepth(txtMEXCSymbol.Text);
end;


procedure TfrmWebSocketClient.btnMEXCFUT_SubscribeKLineClick(Sender: TObject);
begin
  MEXCFUT.SubscribeKLine(txtMEXCSymbol.Text, mexcKlineMin15);
end;


procedure TfrmWebSocketClient.btnMEXCFUT_SubscribeTickerClick(Sender: TObject);
begin
  MEXCFUT.SubscribeTicker(txtMEXCSymbol.Text);
end;


procedure TfrmWebSocketClient.btnMEXCFUT_UnSubscribeDepthClick(Sender: TObject);
begin
  MEXCFUT.UnSubscribeDepth(txtMEXCSymbol.Text);
end;


procedure TfrmWebSocketClient.btnMEXCFUT_UnSubscribeKLineClick(Sender: TObject);
begin
  MEXCFUT.UnSubscribeKLine(txtMEXCSymbol.Text, mexcKlineMin15);
end;


procedure TfrmWebSocketClient.btnMEXCFUT_UnSubscribeTickerClick(Sender: TObject);
begin
  MEXCFUT.UnSubscribeTicker(txtMEXCSymbol.Text);
end;


procedure TfrmWebSocketClient.btnMEXC_SubscribeAccountDealsClick(Sender:
    TObject);
begin
  MEXC.SubscribeAccountDeals;
end;


procedure TfrmWebSocketClient.btnMEXC_SubscribeAccountOrdersClick(Sender:
    TObject);
begin
  MEXC.SubscribeAccountOrders;
end;


procedure TfrmWebSocketClient.btnMEXC_SubscribeAccountUpdateClick(Sender:
    TObject);
begin
  MEXC.SubscribeAccountUpdate;
end;


procedure TfrmWebSocketClient.btnMEXC_SubscribeKLineClick(Sender: TObject);
begin
  MEXC.SubscribeKLine(txtMEXCSymbol.Text);
end;


procedure TfrmWebSocketClient.btnMEXC_SubscribeTradeClick(Sender: TObject);
begin
  MEXC.SubscribeTrade(txtMEXCSymbol.Text);
end;


procedure TfrmWebSocketClient.btnMEXC_UnSubscribeAccountDealsClick(Sender:
    TObject);
begin
  MEXC.UnSubscribeAccountDeals;
end;


procedure TfrmWebSocketClient.btnMEXC_UnSubscribeAccountOrdersClick(Sender:
    TObject);
begin
  MEXC.UnSubscribeAccountOrders;
end;


procedure TfrmWebSocketClient.btnMEXC_UnSubscribeAccountUpdateClick(Sender:
    TObject);
begin
  MEXC.UnSubscribeAccountUpdate;
end;


procedure TfrmWebSocketClient.btnMEXC_UnSubscribeKLineClick(Sender: TObject);
begin
  MEXC.UnSubscribeKLine(txtMEXCSymbol.Text);
end;


procedure TfrmWebSocketClient.btnMEXC_UnSubscribeTradeClick(Sender: TObject);
begin
  MEXC.UnSubscribeTrade(txtMEXCSymbol.Text);
end;


procedure TfrmWebSocketClient.btnMEXCSpotExchangeInformationClick(
  Sender: TObject);
begin
  DoLog(LeftStr(MEXC.REST_API.GetExchangeInformation, 2000));
end;


procedure TfrmWebSocketClient.btnMEXCSpotOrderBookClick(Sender: TObject);
begin
  DoLog(MEXC.REST_API.GetOrderBook(txtMEXCSymbol.Text));
end;


procedure TfrmWebSocketClient.btnMEXCSpotTradesClick(Sender: TObject);
begin
  DoLog(MEXC.REST_API.GetTrades(txtMEXCSymbol.Text));
end;


procedure TfrmWebSocketClient.btnMEXCSpotKlinesClick(Sender: TObject);
begin
  DoLog(MEXC.REST_API.GetKlines(txtMEXCSymbol.Text, '1m'));
end;


procedure TfrmWebSocketClient.btnMEXCSpotAccountInformationClick(
  Sender: TObject);
begin
  DoLog(MEXC.REST_API.GetAccountInformation);
end;


procedure TfrmWebSocketClient.btnMEXCSpotOpenOrdersClick(Sender: TObject);
begin
  DoLog(MEXC.REST_API.GetOpenOrders(txtMEXCSymbol.Text));
end;


procedure TfrmWebSocketClient.btnMEXCFuturesDepthClick(Sender: TObject);
begin
  DoLog(MEXCFUT.REST_API.GetDepth(txtMEXCSymbol.Text));
end;


procedure TfrmWebSocketClient.btnMEXCFuturesDealsClick(Sender: TObject);
begin
  DoLog(MEXCFUT.REST_API.GetDeals(txtMEXCSymbol.Text));
end;


procedure TfrmWebSocketClient.btnMEXCFuturesKlinesClick(Sender: TObject);
begin
  DoLog(MEXCFUT.REST_API.GetKlines(txtMEXCSymbol.Text, 'Min15'));
end;


procedure TfrmWebSocketClient.btnMEXCFuturesIndexPriceClick(Sender: TObject);
begin
  DoLog(MEXCFUT.REST_API.GetIndexPrice(txtMEXCSymbol.Text));
end;


procedure TfrmWebSocketClient.btnMEXCFuturesAccountAssetsClick(
  Sender: TObject);
begin
  DoLog(MEXCFUT.REST_API.GetAccountAssets);
end;


procedure TfrmWebSocketClient.btnMEXCFuturesPositionListClick(Sender: TObject);
begin
  DoLog(MEXCFUT.REST_API.GetPositionList);
end;


procedure TfrmWebSocketClient.btnMEXCGetTradeFeeClick(Sender: TObject);
begin
  DoLog(MEXC.REST_API.GetTradeFee(txtMEXCSymbol.Text));
end;


procedure TfrmWebSocketClient.btnMEXCGetDepositHistoryClick(Sender: TObject);
begin
  DoLog(MEXC.REST_API.GetDepositHistory);
end;


procedure TfrmWebSocketClient.btnMEXCGetAllTickersClick(Sender: TObject);
begin
  DoLog(LeftStr(MEXCFUT.REST_API.GetAllTickers, 2000));
end;


procedure TfrmWebSocketClient.btnMEXCGetOpenPositionsClick(Sender: TObject);
begin
  DoLog(MEXCFUT.REST_API.GetOpenPositions);
end;


procedure TfrmWebSocketClient.btnMEXCSubscribePersonalOrderClick(
  Sender: TObject);
begin
  MEXCFUT.SubscribePersonalOrder;
end;


procedure TfrmWebSocketClient.chkMEXC_UserStreamClick(Sender: TObject);
begin
  MEXC.MEXCUserDataStreams.UserStream := chkMEXC_UserStream.Checked;
end;


procedure TfrmWebSocketClient.DoServerMEXC;
begin
  DoClear;
  MEXC.Client := WSClient;

  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
  chkTLS.Checked := WSClient.TLS;
  chkOverWebSocket.Checked := WSClient.Specifications.RFC6455;

  txtMEXCSymbol.Text := 'BTCUSDT';
end;


procedure TfrmWebSocketClient.DoServerMEXCFUT;
begin
  DoClear;
  MEXCFUT.Client := WSClient;

  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
  chkTLS.Checked := WSClient.TLS;
  chkOverWebSocket.Checked := WSClient.Specifications.RFC6455;

  txtMEXCSymbol.Text := 'BTC_USDT';
end;


procedure TfrmWebSocketClient.FormClose(Sender: TObject;
  var Action: TCloseAction);
begin
  WSClient.Active := False;
end;


procedure TfrmWebSocketClient.MEXCConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.MEXCDisconnect(Connection: TsgcWSConnection;
    Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.MEXCFUTConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.MEXCFUTDisconnect(Connection: TsgcWSConnection;
    Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.MEXCFUTMEXCError(Sender: TObject; const aData,
    aRawMessage: string);
begin
  DoLog('#error: ' + aData);
end;


procedure TfrmWebSocketClient.MEXCFUTMEXCLogin(Sender: TObject; const
    aRawMessage: string);
begin
  DoLog('#login MEXC');
end;


procedure TfrmWebSocketClient.MEXCFUTMEXCMessage(Sender: TObject; const
    aChannel, aRawMessage: string);
begin
  DoLog(aRawMessage);
end;


procedure TfrmWebSocketClient.MEXCFUTMEXCSubscribed(Sender: TObject; const
    aChannel, aRawMessage: string);
begin
  DoLog('#subscribed: ' + aChannel);
end;


procedure TfrmWebSocketClient.MEXCFUTMEXCUnsubscribed(Sender: TObject; const
    aChannel, aRawMessage: string);
begin
  DoLog('#unsubscribed: ' + aChannel);
end;


procedure TfrmWebSocketClient.MEXCMEXCException(Sender: TObject; const E:
    Exception);
begin
  DoLog('#exception: ' + E.Message);
end;


procedure TfrmWebSocketClient.MEXCMEXCMarketStream(Sender: TObject; const
    aMessage: TsgcMEXCSpotProtoMessage; const aStream: TMemoryStream);
var
  i: Integer;
begin
  case aMessage.MessageType of
    sgcmxspmtTrade:
      begin
        for i := 0 to aMessage.Trade.PublicDeals.DealsList.Count - 1 do
        begin
          DoLog('TRADE: ' + TsgcMEXCDealItem(aMessage.Trade.PublicDeals.DealsList[i]).Price);
        end;
      end;
    sgcmxspmtKLine:
      begin
        DoLog('KLINE: ' + aMessage.KLine.PublicSpotKline.ClosingPrice);
      end;
  end;
end;


procedure TfrmWebSocketClient.MEXCMEXCResponse(Sender: TObject; const aId,
    aCode: Int64; const aMessage: string);
begin
  DoLog(aMessage);
end;


procedure TfrmWebSocketClient.MEXCMEXCUserDataStream(Sender: TObject; const
    aChannel, aRawMessage: string);
begin
  DoLog(aRawMessage);
end;


procedure TfrmWebSocketClient.tabMEXCShow(Sender: TObject);
begin
  DoServerMEXC;
end;


procedure TfrmWebSocketClient.tabMEXC_RESTFuturesShow(Sender: TObject);
begin
  DoServerMEXCFUT;
end;


procedure TfrmWebSocketClient.tabMEXC_RESTSpotShow(Sender: TObject);
begin
  DoServerMEXC;
end;


procedure TfrmWebSocketClient.tabMEXC_WebSocketFuturesShow(Sender: TObject);
begin
  DoServerMEXCFUT;
end;


procedure TfrmWebSocketClient.tabMEXC_WebSocketShow(Sender: TObject);
begin
  DoServerMEXC;
end;


procedure TfrmWebSocketClient.txtMEXCApiKeyChange(Sender: TObject);
begin
  MEXC.MEXCAPI.ApiKey := txtMEXCApiKey.Text;
  MEXCFUT.MEXCAPI.ApiKey := txtMEXCApiKey.Text;
end;


procedure TfrmWebSocketClient.txtMEXCApiSecretChange(Sender: TObject);
begin
  MEXC.MEXCAPI.ApiSecret := txtMEXCApiSecret.Text;
  MEXCFUT.MEXCAPI.ApiSecret := txtMEXCApiSecret.Text;
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
  MEXC.Client := nil;
  MEXCFUT.Client := nil;
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

