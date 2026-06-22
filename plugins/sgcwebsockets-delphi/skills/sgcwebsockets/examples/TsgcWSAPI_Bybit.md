# TsgcWSAPI_Bybit - Example

Full source of `uBybit.pas` from the **05.Crypto/14.Bybit** demo, which uses `TsgcWSAPI_Bybit`.

API reference: [TsgcWSAPI_Bybit](../reference/api/TsgcWSAPI_Bybit.md)
Source demo: `05.Crypto/14.Bybit` (file `uBybit.pas`)

```pascal
unit uBybit;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_Bybit, sgcHTTP_API_Bybit;

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
    Bybit: TsgcWSAPI_Bybit;
    tabBybit: TTabSheet;
    Panel9: TPanel;
    Label45: TLabel;
    Label46: TLabel;
    Label84: TLabel;
    txtBybitAPIKey: TEdit;
    txtBybitSymbol: TEdit;
    txtBybitAPISecret: TEdit;
    chkBybitTestNet: TCheckBox;
    PageControl8: TPageControl;
    tabBybitWebSocket: TTabSheet;
    GroupBox15: TGroupBox;
    btnBybitSubscribeOrderBook: TButton;
    btnBybitUnSubscribeKLine: TButton;
    btnBybitUnSubscribeTickers: TButton;
    btnBybitUnSubscribePosition: TButton;
    btnBybitSubscribeTrade: TButton;
    btnBybitSubscribeKLine: TButton;
    btnBybitSubscribeTickers: TButton;
    btnBybitSubscribePosition: TButton;
    btnBybitUnSubscribeOrderBook: TButton;
    btnBybitUnSubscribeTrade: TButton;
    tabBybitRESTApi: TTabSheet;
    btnBybitSubscribeExecution: TButton;
    btnBybitUnSubscribeExecution: TButton;
    btnBybitSubscribeOrder: TButton;
    btnBybitUnSubscribeOrder: TButton;
    GroupBox19: TGroupBox;
    btnBybitRESTGetServerTime: TButton;
    btnBybitOrderBook: TButton;
    btnBybitInstrumentsInfo: TButton;
    btnBybitITickers: TButton;
    btnBybitGetWalletBalance: TButton;
    Label95: TLabel;
    Label115: TLabel;
    cboBybitMarketOrder: TComboBox;
    txtBybitMarketQuantity: TEdit;
    btnBybitMarketOrder: TButton;
    cboBybitLimitOrder: TComboBox;
    Label116: TLabel;
    Label117: TLabel;
    txtBybitLimitQuantity: TEdit;
    Label118: TLabel;
    txtBybitLimitPrice: TEdit;
    btnBybitLimitOrder: TButton;
    btnBybitCancelAllOrders: TButton;
    btnBybitGetPosition: TButton;
    cboBybitClient: TComboBox;
    Label120: TLabel;
    btnBybitSubscribeInsurance: TButton;
    btnBybitUnSubscribeInsurance: TButton;
    btnBybitGetFeeRate: TButton;
    btnBybitGetCoinInfo: TButton;
    btnBybitGetDepositAddress: TButton;
    btnBybitBatchPlaceOrder: TButton;
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnBybitSubscribeExecutionClick(Sender: TObject);
    procedure btnBybitSubscribeKLineClick(Sender: TObject);
    procedure btnBybitSubscribeOrderBookClick(Sender: TObject);
    procedure btnBybitSubscribeOrderClick(Sender: TObject);
    procedure btnBybitSubscribePositionClick(Sender: TObject);
    procedure btnBybitSubscribeTickersClick(Sender: TObject);
    procedure btnBybitSubscribeTradeClick(Sender: TObject);
    procedure btnBybitUnSubscribeExecutionClick(Sender: TObject);
    procedure btnBybitUnSubscribeKLineClick(Sender: TObject);
    procedure btnBybitUnSubscribeOrderBookClick(Sender: TObject);
    procedure btnBybitUnSubscribeOrderClick(Sender: TObject);
    procedure btnBybitUnSubscribePositionClick(Sender: TObject);
    procedure btnBybitUnSubscribeTickersClick(Sender: TObject);
    procedure btnBybitUnSubscribeTradeClick(Sender: TObject);
    procedure btnBybitRESTGetServerTimeClick(Sender: TObject);
    procedure btnBybitCancelAllOrdersClick(Sender: TObject);
    procedure btnBybitLimitOrderClick(Sender: TObject);
    procedure btnBybitMarketOrderClick(Sender: TObject);
    procedure btnBybitOrderBookClick(Sender: TObject);
    procedure btnBybitGetPositionClick(Sender: TObject);
    procedure btnBybitGetWalletBalanceClick(Sender: TObject);
    procedure btnBybitInstrumentsInfoClick(Sender: TObject);
    procedure btnBybitITickersClick(Sender: TObject);
    procedure BybitBybitAuthentication(Sender: TObject; aSuccess: Boolean;
      const aError, aRawMessage: string);
    procedure BybitBybitData(Sender: TObject; const aData: string);
    procedure BybitBybitError(Sender: TObject; aErrorCode: string;
      const aErrorMessage, aRawMessage: string);
    procedure BybitBybitSubscribe(Sender: TObject; const aReqId: string;
      aSuccess: Boolean; const aError, aRawMessage: string);
    procedure BybitBybitUnSubscribe(Sender: TObject; const aReqId: string;
      aSuccess: Boolean; const aError, aRawMessage: string);
    procedure BybitConnect(Connection: TsgcWSConnection);
    procedure BybitDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure cboBybitClientChange(Sender: TObject);
    procedure chkBybitTestNetClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure tabBybitRESTApiShow(Sender: TObject);
    procedure tabBybitWebSocketShow(Sender: TObject);
    procedure txtBybitAPIKeyChange(Sender: TObject);
    procedure txtBybitAPISecretChange(Sender: TObject);
    procedure btnBybitSubscribeInsuranceClick(Sender: TObject);
    procedure btnBybitUnSubscribeInsuranceClick(Sender: TObject);
    procedure btnBybitGetFeeRateClick(Sender: TObject);
    procedure btnBybitGetCoinInfoClick(Sender: TObject);
    procedure btnBybitGetDepositAddressClick(Sender: TObject);
    procedure btnBybitBatchPlaceOrderClick(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServerBybit(aClient: Integer);
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


procedure TfrmWebSocketClient.btnBybitSubscribeExecutionClick(Sender: TObject);
begin
  Bybit.SubscribeExecution;
end;


procedure TfrmWebSocketClient.btnBybitSubscribeKLineClick(Sender: TObject);
begin
  Bybit.SubscribeKLine(txtBybitSymbol.Text);
end;


procedure TfrmWebSocketClient.btnBybitSubscribeOrderBookClick(Sender: TObject);
begin
  Bybit.SubscribeOrderBook(txtBybitSymbol.Text);
end;


procedure TfrmWebSocketClient.btnBybitSubscribeOrderClick(Sender: TObject);
begin
  Bybit.SubscribeOrder;
end;


procedure TfrmWebSocketClient.btnBybitSubscribePositionClick(Sender: TObject);
begin
  Bybit.SubscribePosition;
end;


procedure TfrmWebSocketClient.btnBybitSubscribeTickersClick(Sender: TObject);
begin
  Bybit.SubscribeTicker(txtBybitSymbol.Text);
end;


procedure TfrmWebSocketClient.btnBybitSubscribeTradeClick(Sender: TObject);
begin
  Bybit.SubscribeTrade(txtBybitSymbol.Text);
end;


procedure TfrmWebSocketClient.btnBybitUnSubscribeExecutionClick
  (Sender: TObject);
begin
  Bybit.UnSubscribeExecution;
end;


procedure TfrmWebSocketClient.btnBybitUnSubscribeKLineClick(Sender: TObject);
begin
  Bybit.UnSubscribeKLine(txtBybitSymbol.Text);
end;


procedure TfrmWebSocketClient.btnBybitUnSubscribeOrderBookClick
  (Sender: TObject);
begin
  Bybit.UnSubscribeOrderBook(txtBybitSymbol.Text);
end;


procedure TfrmWebSocketClient.btnBybitUnSubscribeOrderClick(Sender: TObject);
begin
  Bybit.UnSubscribeOrder;
end;


procedure TfrmWebSocketClient.btnBybitUnSubscribePositionClick(Sender: TObject);
begin
  Bybit.UnSubscribePosition;
end;


procedure TfrmWebSocketClient.btnBybitUnSubscribeTickersClick(Sender: TObject);
begin
  Bybit.UnSubscribeTicker(txtBybitSymbol.Text);
end;


procedure TfrmWebSocketClient.btnBybitUnSubscribeTradeClick(Sender: TObject);
begin
  Bybit.UnSubscribeTrade(txtBybitSymbol.Text);
end;


procedure TfrmWebSocketClient.btnBybitRESTGetServerTimeClick(Sender: TObject);
begin
  DoLog(Bybit.REST_API.GetServerTime);
end;


procedure TfrmWebSocketClient.btnBybitCancelAllOrdersClick(Sender: TObject);
begin
  DoLog(Bybit.REST_API.CancelAllOrders(txtBybitSymbol.Text));
end;


procedure TfrmWebSocketClient.btnBybitLimitOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPBybitOrderSide;
begin
  if cboBybitMarketOrder.itemIndex = 0 then
    vSide := bbosBuy
  else
    vSide := bbosSell;

  DoLog(Bybit.REST_API.PlaceLimitOrder(txtBybitSymbol.Text, vSide,
    txtBybitLimitQuantity.Text, txtBybitLimitPrice.Text));
end;


procedure TfrmWebSocketClient.btnBybitMarketOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPBybitOrderSide;
begin
  if cboBybitMarketOrder.itemIndex = 0 then
    vSide := bbosBuy
  else
    vSide := bbosSell;

  DoLog(Bybit.REST_API.PlaceMarketOrder(txtBybitSymbol.Text, vSide,
    txtBybitMarketQuantity.Text));
end;


procedure TfrmWebSocketClient.btnBybitOrderBookClick(Sender: TObject);
begin
  DoLog(Bybit.REST_API.GetOrderBook(txtBybitSymbol.Text));
end;


procedure TfrmWebSocketClient.btnBybitGetPositionClick(Sender: TObject);
begin
  DoLog(Bybit.REST_API.GetPositionInfo(txtBybitSymbol.Text));
end;


procedure TfrmWebSocketClient.btnBybitGetWalletBalanceClick(Sender: TObject);
begin
  DoLog(Bybit.REST_API.GetWalletBalance('SPOT'));
end;


procedure TfrmWebSocketClient.btnBybitInstrumentsInfoClick(Sender: TObject);
begin
  DoLog(Bybit.REST_API.GetInstrumentsInfo(txtBybitSymbol.Text));
end;


procedure TfrmWebSocketClient.btnBybitITickersClick(Sender: TObject);
begin
  DoLog(Bybit.REST_API.GetTickers(txtBybitSymbol.Text));
end;


procedure TfrmWebSocketClient.BybitBybitAuthentication(Sender: TObject;
  aSuccess: Boolean; const aError, aRawMessage: string);
begin
  if aSuccess then
    DoLog('#Bybit Authenticated')
  else
    DoLog('#Bybit Authenticated error: ' + aError);
end;


procedure TfrmWebSocketClient.BybitBybitData(Sender: TObject;
  const aData: string);
begin
  DoLog(aData);
end;


procedure TfrmWebSocketClient.BybitBybitError(Sender: TObject;
  aErrorCode: string; const aErrorMessage, aRawMessage: string);
begin
  DoLog('#Bybit Error: ' + aErrorMessage);
end;


procedure TfrmWebSocketClient.BybitBybitSubscribe(Sender: TObject;
  const aReqId: string; aSuccess: Boolean; const aError, aRawMessage: string);
begin
  if aSuccess then
    DoLog('#Bybit subscribe ok ' + aReqId)
  else
    DoLog('#Bybit subscribe error ' + aError);
end;


procedure TfrmWebSocketClient.BybitBybitUnSubscribe(Sender: TObject;
  const aReqId: string; aSuccess: Boolean; const aError, aRawMessage: string);
begin
  if aSuccess then
    DoLog('#Bybit unsubscribe ok ' + aReqId)
  else
    DoLog('#Bybit unsubscribe error ' + aError);
end;


procedure TfrmWebSocketClient.BybitConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.BybitDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.cboBybitClientChange(Sender: TObject);
begin
  DoServerBybit(cboBybitClient.itemIndex);
end;


procedure TfrmWebSocketClient.chkBybitTestNetClick(Sender: TObject);
begin
  Bybit.Bybit.TestNet := chkBybitTestNet.Checked;

  DoServerBybit(PageControl8.ActivePageIndex);
end;


procedure TfrmWebSocketClient.DoServerBybit(aClient: Integer);
begin
  DoClear;
  Bybit.Client := WSClient;
  case aClient of
    0:
      Bybit.BybitClient := bybSpot;
    1:
      Bybit.BybitClient := bybLinear;
    2:
      Bybit.BybitClient := bybInverse;
    3:
      Bybit.BybitClient := bybOption;
  end;

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


procedure TfrmWebSocketClient.tabBybitRESTApiShow(Sender: TObject);
begin
  DoServerBybit(1);
end;


procedure TfrmWebSocketClient.tabBybitWebSocketShow(Sender: TObject);
begin
  DoServerBybit(0);
end;


procedure TfrmWebSocketClient.txtBybitAPIKeyChange(Sender: TObject);
begin
  Bybit.Bybit.ApiKey := txtBybitAPIKey.Text;
  DoServerBybit(PageControl8.ActivePageIndex);
end;


procedure TfrmWebSocketClient.txtBybitAPISecretChange(Sender: TObject);
begin
  Bybit.Bybit.ApiSecret := txtBybitAPISecret.Text;
  DoServerBybit(PageControl8.ActivePageIndex);
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
  Bybit.Client := nil;
end;

procedure TfrmWebSocketClient.DoBeforeConnect;
begin
end;

procedure TfrmWebSocketClient.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
end;


procedure TfrmWebSocketClient.btnBybitSubscribeInsuranceClick(Sender: TObject);
begin
  Bybit.SubscribeInsurance;
end;


procedure TfrmWebSocketClient.btnBybitUnSubscribeInsuranceClick
  (Sender: TObject);
begin
  Bybit.UnSubscribeInsurance;
end;


procedure TfrmWebSocketClient.btnBybitGetFeeRateClick(Sender: TObject);
begin
  DoLog(Bybit.REST_API.GetFeeRate);
end;


procedure TfrmWebSocketClient.btnBybitGetCoinInfoClick(Sender: TObject);
begin
  DoLog(Bybit.REST_API.GetCoinInfo);
end;


procedure TfrmWebSocketClient.btnBybitGetDepositAddressClick(Sender: TObject);
begin
  DoLog(Bybit.REST_API.GetDepositAddress('BTC'));
end;


procedure TfrmWebSocketClient.btnBybitBatchPlaceOrderClick(Sender: TObject);
begin
  DoLog('#BatchPlaceOrder placeholder - requires order JSON configuration');
end;

end.
```

