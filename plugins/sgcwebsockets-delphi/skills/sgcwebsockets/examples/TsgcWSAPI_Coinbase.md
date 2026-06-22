# TsgcWSAPI_Coinbase - Example

Full source of `uCoinbase.pas` from the **05.Crypto/09.Coinbase** demo, which uses `TsgcWSAPI_Coinbase`.

API reference: [TsgcWSAPI_Coinbase](../reference/api/TsgcWSAPI_Coinbase.md)
Source demo: `05.Crypto/09.Coinbase` (file `uCoinbase.pas`)

```pascal
unit uCoinbase;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_Coinbase, sgcHTTP_API_Coinbase;

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
    COINBASE: TsgcWSAPI_Coinbase;
    tabCOINBASE: TTabSheet;
    btnCoinbaseSubscribeHeartBeat: TButton;
    btnCoinbaseUnSubscribeHeartBeat: TButton;
    btnCoinbaseSubscribeStatus: TButton;
    btnCoinbaseUnSubscribeStatus: TButton;
    Label51: TLabel;
    txtCoinbaseProductId: TEdit;
    btnCoinbaseSubscribeTicker: TButton;
    btnCoinbaseUnSubscribeTicker: TButton;
    btnCoinbaseSubscribeLevel2: TButton;
    btnCoinbaseUnSubscribeLevel2: TButton;
    Label52: TLabel;
    txtCoinbaseApiKey: TEdit;
    Label53: TLabel;
    txtCoinbaseApiSecret: TEdit;
    btnCoinbaseSubscribeUser: TButton;
    btnCoinbaseUnSubscribeUser: TButton;
    chkCoinbaseSandbox: TCheckBox;
    PageControl4: TPageControl;
    tabCoinbaseWebSocket: TTabSheet;
    tabCoinbaseRestPrivate: TTabSheet;
    btnCoinbaseRestListAccounts: TButton;
    tabCoinbaseRestPublic: TTabSheet;
    btnCoinbaseListOrders: TButton;
    btnCoinbaseGetProducts: TButton;
    btnCoinbaseGetProduct: TButton;
    btnCoinbaseGetOrderBook: TButton;
    btnCoinbaseGetCandles: TButton;
    btnCoinbaseGetTrades: TButton;
    Button16: TButton;
    btnCoinbaseMarketOrder: TButton;
    cboCoinbaseMarketOrderSide: TComboBox;
    cboCoinbaseLimitOrderSide: TComboBox;
    btnCoinbaseLimitOrder: TButton;
    Label55: TLabel;
    Label56: TLabel;
    Label57: TLabel;
    Label58: TLabel;
    Label59: TLabel;
    Label60: TLabel;
    Label62: TLabel;
    Label63: TLabel;
    txtCoinbaseMarketOrderAmount: TEdit;
    txtCoinbaseLimitOrderAmount: TEdit;
    txtCoinbaseLimitOrderPrice: TEdit;
    btnCoinbaseListProducts: TButton;
    btnCoinbaseGetTransactionSummary: TButton;
    btnCoinbaseListPortfolios: TButton;
    btnCoinbaseGetBestBidAsk: TButton;
    chkCoinbaseWebSocketUser: TCheckBox;
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnCoinbaseGetOrderBookClick(Sender: TObject);
    procedure btnCoinbaseGetProductClick(Sender: TObject);
    procedure btnCoinbaseListOrdersClick(Sender: TObject);
    procedure btnCoinbaseGetProductsClick(Sender: TObject);
    procedure btnCoinbaseGetCandlesClick(Sender: TObject);
    procedure btnCoinbaseGetTradesClick(Sender: TObject);
    procedure btnCoinbaseLimitOrderClick(Sender: TObject);
    procedure btnCoinbaseListProductsClick(Sender: TObject);
    procedure btnCoinbaseGetTransactionSummaryClick(Sender: TObject);
    procedure btnCoinbaseListPortfoliosClick(Sender: TObject);
    procedure btnCoinbaseGetBestBidAskClick(Sender: TObject);
    procedure btnCoinbaseMarketOrderClick(Sender: TObject);
    procedure btnCoinbaseRestListAccountsClick(Sender: TObject);
    procedure btnCoinbaseSubscribeHeartBeatClick(Sender: TObject);
    procedure btnCoinbaseSubscribeLevel2Click(Sender: TObject);
    procedure btnCoinbaseSubscribeStatusClick(Sender: TObject);
    procedure btnCoinbaseSubscribeTickerClick(Sender: TObject);
    procedure btnCoinbaseUnSubscribeHeartBeatClick(Sender: TObject);
    procedure btnCoinbaseUnSubscribeLevel2Click(Sender: TObject);
    procedure btnCoinbaseUnSubscribeStatusClick(Sender: TObject);
    procedure btnCoinbaseUnSubscribeTickerClick(Sender: TObject);
    procedure btnCoinbaseSubscribeUserClick(Sender: TObject);
    procedure btnCoinbaseUnSubscribeUserClick(Sender: TObject);
    procedure Button16Click(Sender: TObject);
    procedure chkCoinbaseSandboxClick(Sender: TObject);
    procedure chkCoinbaseWebSocketUserClick(Sender: TObject);
    procedure COINBASECoinbaseError(Sender: TObject;
      aError, aReason, aRawMessage: string);
    procedure COINBASECoinbaseHTTPException(Sender: TObject; E: Exception);
    procedure COINBASECoinbaseMessage(Sender: TObject;
      aType, aRawMessage: string);
    procedure COINBASECoinbaseSubscriptions(Sender: TObject;
      aSubscription: string);
    procedure COINBASEconnect(Connection: TsgcWSConnection);
    procedure COINBASEDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure tabCOINBASEShow(Sender: TObject);
    procedure txtCoinbaseApiKeyChange(Sender: TObject);
    procedure txtCoinbaseApiSecretChange(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServerCOINBASE;
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


procedure TfrmWebSocketClient.btnCoinbaseGetOrderBookClick(Sender: TObject);
begin
  DoLog(COINBASE.REST_API.GetPublicProductBook(txtCoinbaseProductId.Text));
end;


procedure TfrmWebSocketClient.btnCoinbaseGetProductClick(Sender: TObject);
begin
  DoLog(COINBASE.REST_API.GetPublicProduct(txtCoinbaseProductId.Text));
end;


procedure TfrmWebSocketClient.btnCoinbaseListOrdersClick(Sender: TObject);
begin
  DoLog(COINBASE.REST_API.ListOrders);
end;


procedure TfrmWebSocketClient.btnCoinbaseGetProductsClick(Sender: TObject);
begin
  DoLog(COINBASE.REST_API.GetPublicProducts);
end;


procedure TfrmWebSocketClient.btnCoinbaseGetCandlesClick(Sender: TObject);
begin
  DoLog(COINBASE.REST_API.GetPublicProductCandles(txtCoinbaseProductId.Text,
    Trunc(Now), Now, cgr5m));
end;


procedure TfrmWebSocketClient.btnCoinbaseGetTradesClick(Sender: TObject);
begin
  DoLog(COINBASE.REST_API.GetTrades(txtCoinbaseProductId.Text));
end;


procedure TfrmWebSocketClient.btnCoinbaseLimitOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPCoinbaseOrderSide;
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  if cboCoinbaseLimitOrderSide.itemIndex = 0 then
    vSide := coisBuy
  else
    vSide := coisSell;

  DoLog(COINBASE.REST_API.PlaceLimitOrder(vSide, txtCoinbaseProductId.Text,
    StrToFloat(txtCoinbaseLimitOrderAmount.Text, vFS), 0,
    StrToFloat(txtCoinbaseLimitOrderPrice.Text, vFS)));
end;


procedure TfrmWebSocketClient.btnCoinbaseListProductsClick(Sender: TObject);
begin
  DoLog(COINBASE.REST_API.ListProducts);
end;


procedure TfrmWebSocketClient.btnCoinbaseGetTransactionSummaryClick(Sender: TObject);
begin
  DoLog(COINBASE.REST_API.GetTransactionSummary);
end;


procedure TfrmWebSocketClient.btnCoinbaseListPortfoliosClick(Sender: TObject);
begin
  DoLog(COINBASE.REST_API.ListPortfolios);
end;


procedure TfrmWebSocketClient.btnCoinbaseGetBestBidAskClick(Sender: TObject);
begin
  DoLog(COINBASE.REST_API.GetBestBidAsk);
end;


procedure TfrmWebSocketClient.btnCoinbaseMarketOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPCoinbaseOrderSide;
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  if cboCoinbaseMarketOrderSide.itemIndex = 0 then
    vSide := coisBuy
  else
    vSide := coisSell;

  DoLog(COINBASE.REST_API.PlaceMarketOrder(vSide, txtCoinbaseProductId.Text,
    StrToFloat(txtCoinbaseMarketOrderAmount.Text, vFS), 0));
end;


procedure TfrmWebSocketClient.btnCoinbaseRestListAccountsClick(Sender: TObject);
begin
  DoLog(COINBASE.REST_API.ListAccounts);
end;


procedure TfrmWebSocketClient.btnCoinbaseSubscribeHeartBeatClick
  (Sender: TObject);
begin
  COINBASE.SubscribeHeartBeat;
end;


procedure TfrmWebSocketClient.btnCoinbaseSubscribeLevel2Click(Sender: TObject);
begin
  COINBASE.SubscribeLevel2(txtCoinbaseProductId.Text);
end;


procedure TfrmWebSocketClient.btnCoinbaseSubscribeStatusClick(Sender: TObject);
begin
  COINBASE.SubscribeStatus(txtCoinbaseProductId.Text);
end;


procedure TfrmWebSocketClient.btnCoinbaseSubscribeTickerClick(Sender: TObject);
begin
  COINBASE.SubscribeTicker(txtCoinbaseProductId.Text);
end;


procedure TfrmWebSocketClient.btnCoinbaseUnSubscribeHeartBeatClick
  (Sender: TObject);
begin
  COINBASE.UnSubscribeHeartBeat;
end;


procedure TfrmWebSocketClient.btnCoinbaseUnSubscribeLevel2Click
  (Sender: TObject);
begin
  COINBASE.UnSubscribeLevel2(txtCoinbaseProductId.Text);
end;


procedure TfrmWebSocketClient.btnCoinbaseUnSubscribeStatusClick
  (Sender: TObject);
begin
  COINBASE.UnSubscribeStatus(txtCoinbaseProductId.Text);
end;


procedure TfrmWebSocketClient.btnCoinbaseUnSubscribeTickerClick
  (Sender: TObject);
begin
  COINBASE.UnSubscribeTicker(txtCoinbaseProductId.Text);
end;


procedure TfrmWebSocketClient.btnCoinbaseSubscribeUserClick(Sender: TObject);
begin
  COINBASE.SubscribeUser(txtCoinbaseProductId.Text);
end;


procedure TfrmWebSocketClient.btnCoinbaseUnSubscribeUserClick(Sender: TObject);
begin
  COINBASE.UnSubscribeUser(txtCoinbaseProductId.Text);
end;


procedure TfrmWebSocketClient.Button16Click(Sender: TObject);
begin
  DoLog(COINBASE.REST_API.GetTime);
end;


procedure TfrmWebSocketClient.chkCoinbaseSandboxClick(Sender: TObject);
begin
  COINBASE.COINBASE.SandBox := chkCoinbaseSandbox.Checked;
  DoServerCOINBASE;
end;


procedure TfrmWebSocketClient.chkCoinbaseWebSocketUserClick(Sender: TObject);
begin
  Coinbase.Coinbase.UserEndpoint := chkCoinbaseWebSocketUser.Checked;
  tabCoinbaseShow(nil);
end;


procedure TfrmWebSocketClient.COINBASECoinbaseError(Sender: TObject;
  aError, aReason, aRawMessage: string);
begin
  DoLog('#coinbase error: ' + aError + ' ' + aReason);
end;


procedure TfrmWebSocketClient.COINBASECoinbaseHTTPException(Sender: TObject;
  E: Exception);
begin
  DoLog('#coinbase HTTP exception: ' + E.Message);
end;


procedure TfrmWebSocketClient.COINBASECoinbaseMessage(Sender: TObject;
  aType, aRawMessage: string);
begin
  DoLog('#coinbase message: ' + aRawMessage);
end;


procedure TfrmWebSocketClient.COINBASECoinbaseSubscriptions(Sender: TObject;
  aSubscription: string);
begin
  DoLog('#coinbase subscriptions: ' + aSubscription);
end;


procedure TfrmWebSocketClient.COINBASEconnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected coinbase');
end;


procedure TfrmWebSocketClient.COINBASEDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected coinbase');
end;


procedure TfrmWebSocketClient.DoServerCOINBASE;
begin
  DoClear;
  COINBASE.Client := WSClient;

  txtParameters.Text := '/';
  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  chkTLS.Checked := WSClient.TLS;
  chkOverWebSocket.Checked := WSClient.Specifications.RFC6455;
end;


procedure TfrmWebSocketClient.FormClose(Sender: TObject;
  var Action: TCloseAction);
begin
  WSClient.Active := False;
end;


procedure TfrmWebSocketClient.tabCOINBASEShow(Sender: TObject);
begin
  DoServerCOINBASE;
end;


procedure TfrmWebSocketClient.txtCoinbaseApiKeyChange(Sender: TObject);
begin
  COINBASE.COINBASE.ApiKey := txtCoinbaseApiKey.Text;
end;


procedure TfrmWebSocketClient.txtCoinbaseApiSecretChange(Sender: TObject);
begin
  COINBASE.COINBASE.ApiSecret := txtCoinbaseApiSecret.Text;
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
  COINBASE.Client := nil;
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

