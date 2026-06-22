# TsgcWSAPI_Bitmex - Example

Full source of `uBitmex.pas` from the **05.Crypto/06.Bitmex** demo, which uses `TsgcWSAPI_Bitmex`.

API reference: [TsgcWSAPI_Bitmex](../reference/api/TsgcWSAPI_Bitmex.md)
Source demo: `05.Crypto/06.Bitmex` (file `uBitmex.pas`)

```pascal
unit uBitmex;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_Bitmex, sgcHTTP_API_Bitmex;

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
    tabBITMEX: TTabSheet;
    BITMEX: TsgcWSAPI_Bitmex;
    Label36: TLabel;
    txtBitmexApiKey: TEdit;
    Label37: TLabel;
    txtBitmexApiSecret: TEdit;
    btnBitmexAuthenticate: TButton;
    pageControlBitmex: TPageControl;
    tabBitmexWS: TTabSheet;
    Label34: TLabel;
    cboBitmexTopics: TComboBox;
    btnBitmexSubscribe: TButton;
    btnBitmexUnsubscribe: TButton;
    tabBitmexREST: TTabSheet;
    btnBitmexGetExecutions: TButton;
    btnBitmexGetOrderBook: TButton;
    Label35: TLabel;
    txtBitmexSymbol: TEdit;
    btnBitmexGetPosition: TButton;
    btnBitmexGetQuote: TButton;
    btnBitmexGetInstrument: TButton;
    btnBitmexGetOrders: TButton;
    Label96: TLabel;
    cboBitmexMarketOrderSide: TComboBox;
    Label97: TLabel;
    txtBitmexMarketOrderSize: TEdit;
    cboBitmexMarketOrder: TButton;
    cboBitmexLimitOrderSide: TComboBox;
    Label98: TLabel;
    txtBitmexLimitOrderSize: TEdit;
    Label99: TLabel;
    Label100: TLabel;
    txtBitmexLimitOrderPrice: TEdit;
    cboBitmexLimitOrder: TButton;
    btnBitmexCancelAllOrders: TButton;
    chkBitmexTestNet: TCheckBox;
    btnBitmexGetFunding: TButton;
    btnBitmexGetInsurance: TButton;
    btnBitmexGetUserWallet: TButton;
    btnBitmexGetUserMargin: TButton;
    btnBitmexCancelAllAfter: TButton;
    procedure BITMEXBitmexAuthenticated(Sender: TObject);
    procedure BITMEXBitmexConnect(Sender: TObject; const aMessage: string);
    procedure BITMEXBitmexError(Sender: TObject; const aMessage: string);
    procedure BITMEXBitmexMessage(Sender: TObject;
      const aTopic: TwsBitmexTopics; const aMessage: string);
    procedure BITMEXBitmexSubscribed(Sender: TObject; const aChannel: string);
    procedure BITMEXBitmexUnsubscribed(Sender: TObject; const aChannel: string);
    procedure BITMEXConnect(Connection: TsgcWSConnection);
    procedure BITMEXDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure btnBitmexSubscribeClick(Sender: TObject);
    procedure btnBitmexUnsubscribeClick(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnBitmexAuthenticateClick(Sender: TObject);
    procedure btnBitmexCancelAllOrdersClick(Sender: TObject);
    procedure btnBitmexGetExecutionsClick(Sender: TObject);
    procedure btnBitmexGetInstrumentClick(Sender: TObject);
    procedure btnBitmexGetOrderBookClick(Sender: TObject);
    procedure btnBitmexGetOrdersClick(Sender: TObject);
    procedure btnBitmexGetPositionClick(Sender: TObject);
    procedure btnBitmexGetQuoteClick(Sender: TObject);
    procedure cboBitmexLimitOrderClick(Sender: TObject);
    procedure cboBitmexMarketOrderClick(Sender: TObject);
    procedure btnBitmexGetFundingClick(Sender: TObject);
    procedure btnBitmexGetInsuranceClick(Sender: TObject);
    procedure btnBitmexGetUserWalletClick(Sender: TObject);
    procedure btnBitmexGetUserMarginClick(Sender: TObject);
    procedure btnBitmexCancelAllAfterClick(Sender: TObject);
    procedure chkBitmexTestNetClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure tabBITMEXShow(Sender: TObject);
    procedure txtBitmexApiKeyChange(Sender: TObject);
    procedure txtBitmexApiSecretChange(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServerBITMEX;
  end;

var
  frmWebSocketClient: TfrmWebSocketClient;

implementation

uses
  sgcWebSocket_Helpers, sgcJSON, StrUtils, sgcBase_Helpers,
  ShellAPI, DateUtils;
{$R *.dfm}

procedure TfrmWebSocketClient.BITMEXBitmexAuthenticated(Sender: TObject);
begin
  DoLog('#Bitmex Authenticated');
end;


procedure TfrmWebSocketClient.BITMEXBitmexConnect(Sender: TObject;
  const aMessage: string);
begin
  DoLog('#Bitmex Connected: ' + aMessage);
end;


procedure TfrmWebSocketClient.BITMEXBitmexError(Sender: TObject;
  const aMessage: string);
begin
  DoLog('Bitmex Error: ' + aMessage);
end;


procedure TfrmWebSocketClient.BITMEXBitmexMessage(Sender: TObject;
  const aTopic: TwsBitmexTopics; const aMessage: string);
begin
  DoLog('Bitmex Message: ' + aMessage);
end;


procedure TfrmWebSocketClient.BITMEXBitmexSubscribed(Sender: TObject;
  const aChannel: string);
begin
  DoLog('Bitmex Subscribed: ' + aChannel);
end;


procedure TfrmWebSocketClient.BITMEXBitmexUnsubscribed(Sender: TObject;
  const aChannel: string);
begin
  DoLog('Bitmex Unsubscribed: ' + aChannel);
end;


procedure TfrmWebSocketClient.BITMEXConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.BITMEXDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.btnBitmexSubscribeClick(Sender: TObject);
begin
  BITMEX.Subscribe(TwsBitmexTopics(cboBitmexTopics.itemIndex),
    txtBitmexSymbol.Text);
end;


procedure TfrmWebSocketClient.btnBitmexUnsubscribeClick(Sender: TObject);
begin
  BITMEX.Unsubscribe(TwsBitmexTopics(cboBitmexTopics.itemIndex),
    txtBitmexSymbol.Text);
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


procedure TfrmWebSocketClient.btnBitmexAuthenticateClick(Sender: TObject);
begin
  BITMEX.BITMEX.ApiKey := txtBitmexApiKey.Text;
  BITMEX.BITMEX.ApiSecret := txtBitmexApiSecret.Text;
  BITMEX.Authenticate;
end;


procedure TfrmWebSocketClient.btnBitmexCancelAllOrdersClick(Sender: TObject);
begin
  DoLog(BITMEX.REST_API.CancelAllOrders(txtBitmexSymbol.Text));
end;


procedure TfrmWebSocketClient.btnBitmexGetExecutionsClick(Sender: TObject);
begin
  DoLog(BITMEX.REST_API.GetExecutions);
end;


procedure TfrmWebSocketClient.btnBitmexGetInstrumentClick(Sender: TObject);
begin
  DoLog(BITMEX.REST_API.GetInstruments(txtBitmexSymbol.Text));
end;


procedure TfrmWebSocketClient.btnBitmexGetOrderBookClick(Sender: TObject);
begin
  DoLog(BITMEX.REST_API.GetOrderBook(txtBitmexSymbol.Text));
end;


procedure TfrmWebSocketClient.btnBitmexGetOrdersClick(Sender: TObject);
begin
  DoLog(BITMEX.REST_API.GetOrders(txtBitmexSymbol.Text));
end;


procedure TfrmWebSocketClient.btnBitmexGetPositionClick(Sender: TObject);
begin
  DoLog(BITMEX.REST_API.GetPosition);
end;


procedure TfrmWebSocketClient.btnBitmexGetQuoteClick(Sender: TObject);
begin
  DoLog(BITMEX.REST_API.GetQuotes(txtBitmexSymbol.Text));
end;


procedure TfrmWebSocketClient.cboBitmexLimitOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPBitmexOrderSide;
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  if cboBitmexLimitOrderSide.itemIndex = 0 then
    vSide := bmosBuy
  else
    vSide := bmosSell;

  DoLog(BITMEX.REST_API.PlaceLimitOrder(vSide, txtBitmexSymbol.Text,
    StrToFloat(txtBitmexLimitOrderSize.Text, vFS),
    StrToFloat(txtBitmexLimitOrderPrice.Text, vFS)));
end;


procedure TfrmWebSocketClient.cboBitmexMarketOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPBitmexOrderSide;
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  if cboBitmexMarketOrderSide.itemIndex = 0 then
    vSide := bmosBuy
  else
    vSide := bmosSell;

  DoLog(BITMEX.REST_API.PlaceMarketOrder(vSide, txtBitmexSymbol.Text,
    StrToFloat(txtBitmexMarketOrderSize.Text, vFS)));
end;


procedure TfrmWebSocketClient.btnBitmexGetFundingClick(Sender: TObject);
begin
  DoLog(BITMEX.REST_API.GetFunding(txtBitmexSymbol.Text));
end;


procedure TfrmWebSocketClient.btnBitmexGetInsuranceClick(Sender: TObject);
begin
  DoLog(BITMEX.REST_API.GetInsurance);
end;


procedure TfrmWebSocketClient.btnBitmexGetUserWalletClick(Sender: TObject);
begin
  DoLog(BITMEX.REST_API.GetUserWallet);
end;


procedure TfrmWebSocketClient.btnBitmexGetUserMarginClick(Sender: TObject);
begin
  DoLog(BITMEX.REST_API.GetUserMargin);
end;


procedure TfrmWebSocketClient.btnBitmexCancelAllAfterClick(Sender: TObject);
begin
  BITMEX.CancelAllAfter(60000);
end;


procedure TfrmWebSocketClient.chkBitmexTestNetClick(Sender: TObject);
begin
  BITMEX.BITMEX.TestNet := chkBitmexTestNet.Checked;

  tabBITMEXShow(nil);
end;


procedure TfrmWebSocketClient.DoServerBITMEX;
begin
  DoClear;
  BITMEX.Client := WSClient;
  if BITMEX.BITMEX.ApiKey = '' then
    BITMEX.BITMEX.ApiKey := txtBitmexApiKey.Text;
  if BITMEX.BITMEX.ApiSecret = '' then
    BITMEX.BITMEX.ApiSecret := txtBitmexApiSecret.Text;

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


procedure TfrmWebSocketClient.tabBITMEXShow(Sender: TObject);
begin
  DoServerBITMEX;
end;


procedure TfrmWebSocketClient.txtBitmexApiKeyChange(Sender: TObject);
begin
  BITMEX.BITMEX.ApiKey := txtBitmexApiKey.Text;
end;


procedure TfrmWebSocketClient.txtBitmexApiSecretChange(Sender: TObject);
begin
  BITMEX.BITMEX.ApiSecret := txtBitmexApiSecret.Text;
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
  BITMEX.Client := nil;
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

