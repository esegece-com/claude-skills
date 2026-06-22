# TsgcWSAPI_OKX - Example

Full source of `uOKX.pas` from the **05.Crypto/12.OKX** demo, which uses `TsgcWSAPI_OKX`.

API reference: [TsgcWSAPI_OKX](../reference/api/TsgcWSAPI_OKX.md)
Source demo: `05.Crypto/12.OKX` (file `uOKX.pas`)

```pascal
unit uOKX;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_OKX;

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
    OKX: TsgcWSAPI_OKX;
    tabOKX: TTabSheet;
    Panel5: TPanel;
    Label1: TLabel;
    Label2: TLabel;
    Label6: TLabel;
    Label11: TLabel;
    txtOkxApiKey: TEdit;
    txtOkxInstId: TEdit;
    txtOkxApiSecret: TEdit;
    chkOkxIsDemo: TCheckBox;
    txtOkxPassphrase: TEdit;
    PageControl6: TPageControl;
    tabOKXMethods: TTabSheet;
    Panel6: TPanel;
    GroupBox11: TGroupBox;
    Label12: TLabel;
    Label13: TLabel;
    Label15: TLabel;
    Label16: TLabel;
    Label17: TLabel;
    btnOkxSubscribeAccount: TButton;
    btnOkxUnSubscribeAccount: TButton;
    btnOkxSubscribeOrders: TButton;
    btnOkxUnSubscribeOrders: TButton;
    cboOkxMarketSide: TComboBox;
    txtOkxMarketSize: TEdit;
    cboOkxMarketOrder: TButton;
    cboOkxLimitSide: TComboBox;
    txtOkxLimitSize: TEdit;
    txtOkxLimitPrice: TEdit;
    cboOkxLimitOrder: TButton;
    Panel7: TPanel;
    GroupBox12: TGroupBox;
    btnOkxSubscribeInstruments: TButton;
    btnOkxUnSubscribeCandlesticks: TButton;
    btnOkxUnSubscribeTradeOrders: TButton;
    btnOkxUnSubscribeOrderBook: TButton;
    btnOkxUnSubscribeStatus: TButton;
    btnOkxSubscribeTicker: TButton;
    btnOkxSubscribeCandlesticks: TButton;
    btnOkxSubscribeTradeOrders: TButton;
    btnOkxSubscribeOrderBook: TButton;
    btnOkxSubscribeStatus: TButton;
    btnOkxUnSubscribeInstruments: TButton;
    btnOkxUnSubscribeTicker: TButton;
    chkOkxIsPrivate: TCheckBox;
    btnOKXSubscribeAllTrades: TButton;
    btnOKXUnSubscribeAllTrades: TButton;
    btnOKXSubscribeFills: TButton;
    btnOKXUnSubscribeFills: TButton;
    btnOKXBatchPlaceOrders: TButton;
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnOkxSubscribeAccountClick(Sender: TObject);
    procedure btnOkxSubscribeInstrumentsClick(Sender: TObject);
    procedure btnOkxSubscribeTickerClick(Sender: TObject);
    procedure btnOkxUnSubscribeInstrumentsClick(Sender: TObject);
    procedure btnOkxUnSubscribeTickerClick(Sender: TObject);
    procedure btnOkxUnSubscribeCandlesticksClick(Sender: TObject);
    procedure btnOkxSubscribeCandlesticksClick(Sender: TObject);
    procedure btnOkxSubscribeTradeOrdersClick(Sender: TObject);
    procedure btnOkxUnSubscribeTradeOrdersClick(Sender: TObject);
    procedure btnOkxUnSubscribeOrderBookClick(Sender: TObject);
    procedure btnOkxSubscribeOrderBookClick(Sender: TObject);
    procedure btnOkxSubscribeOrdersClick(Sender: TObject);
    procedure btnOkxSubscribeStatusClick(Sender: TObject);
    procedure btnOkxUnSubscribeAccountClick(Sender: TObject);
    procedure btnOkxUnSubscribeOrdersClick(Sender: TObject);
    procedure btnOkxUnSubscribeStatusClick(Sender: TObject);
    procedure cboOkxMarketOrderClick(Sender: TObject);
    procedure cboOkxLimitOrderClick(Sender: TObject);
    procedure chkOkxIsDemoClick(Sender: TObject);
    procedure chkOkxIsPrivateClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure OKXConnect(Connection: TsgcWSConnection);
    procedure OKXDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure OKXOKXConnect(Sender: TObject;
      aMessage, aCode, aRawMessage: string);
    procedure OKXOKXError(Sender: TObject;
      aCode, aMessage, aRawMessage: string);
    procedure OKXOKXMessage(Sender: TObject; aType, aRawMessage: string);
    procedure OKXOKXSubscribed(Sender: TObject;
      aChannel, aInstId, aRawMessage: string);
    procedure OKXOKXUnsubscribed(Sender: TObject;
      aChannel, aInstId, aRawMessage: string);
    procedure tabOKXShow(Sender: TObject);
    procedure txtOkxApiKeyChange(Sender: TObject);
    procedure txtOkxApiSecretChange(Sender: TObject);
    procedure txtOkxPassphraseChange(Sender: TObject);
    procedure btnOKXSubscribeAllTradesClick(Sender: TObject);
    procedure btnOKXUnSubscribeAllTradesClick(Sender: TObject);
    procedure btnOKXSubscribeFillsClick(Sender: TObject);
    procedure btnOKXUnSubscribeFillsClick(Sender: TObject);
    procedure btnOKXBatchPlaceOrdersClick(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServerOKX;
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


procedure TfrmWebSocketClient.btnOkxSubscribeAccountClick(Sender: TObject);
begin
  OKX.SubscribeAccount;
end;


procedure TfrmWebSocketClient.btnOkxSubscribeInstrumentsClick(Sender: TObject);
begin
  OKX.SubscribeInstruments;
end;


procedure TfrmWebSocketClient.btnOkxSubscribeTickerClick(Sender: TObject);
begin
  OKX.SubscribeTicker(txtOkxInstId.Text);
end;


procedure TfrmWebSocketClient.btnOkxUnSubscribeInstrumentsClick
  (Sender: TObject);
begin
  OKX.UnSubscribeInstruments;
end;


procedure TfrmWebSocketClient.btnOkxUnSubscribeTickerClick(Sender: TObject);
begin
  OKX.UnSubscribeTicker(txtOkxInstId.Text);
end;


procedure TfrmWebSocketClient.btnOkxUnSubscribeCandlesticksClick
  (Sender: TObject);
begin
  OKX.UnSubscribeCandlestick(txtOkxInstId.Text);
end;


procedure TfrmWebSocketClient.btnOkxSubscribeCandlesticksClick(Sender: TObject);
begin
  OKX.SubscribeCandlestick(txtOkxInstId.Text);
end;


procedure TfrmWebSocketClient.btnOkxSubscribeTradeOrdersClick(Sender: TObject);
begin
  OKX.SubscribeTrades(txtOkxInstId.Text);
end;


procedure TfrmWebSocketClient.btnOkxUnSubscribeTradeOrdersClick
  (Sender: TObject);
begin
  OKX.UnSubscribeTrades(txtOkxInstId.Text);
end;


procedure TfrmWebSocketClient.btnOkxUnSubscribeOrderBookClick(Sender: TObject);
begin
  OKX.UnSubscribeOrderBook(txtOkxInstId.Text);
end;


procedure TfrmWebSocketClient.btnOkxSubscribeOrderBookClick(Sender: TObject);
begin
  OKX.SubscribeOrderBook(txtOkxInstId.Text);
end;


procedure TfrmWebSocketClient.btnOkxSubscribeOrdersClick(Sender: TObject);
begin
  OKX.SubscribeOrders;
end;


procedure TfrmWebSocketClient.btnOkxSubscribeStatusClick(Sender: TObject);
begin
  OKX.SubscribeStatus;
end;


procedure TfrmWebSocketClient.btnOkxUnSubscribeAccountClick(Sender: TObject);
begin
  OKX.UnSubscribeAccount;
end;


procedure TfrmWebSocketClient.btnOkxUnSubscribeOrdersClick(Sender: TObject);
begin
  OKX.UnSubscribeOrders;
end;


procedure TfrmWebSocketClient.btnOkxUnSubscribeStatusClick(Sender: TObject);
begin
  OKX.UnSubscribeStatus;
end;


procedure TfrmWebSocketClient.cboOkxMarketOrderClick(Sender: TObject);
var
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  case cboOkxMarketSide.itemIndex of
    0:
      OKX.PlaceMarketOrder(okxosBuy, txtOkxInstId.Text,
        StrToFloat(txtOkxMarketSize.Text, vFS));
    1:
      OKX.PlaceMarketOrder(okxosSell, txtOkxInstId.Text,
        StrToFloat(txtOkxMarketSize.Text, vFS));
  end;
end;


procedure TfrmWebSocketClient.cboOkxLimitOrderClick(Sender: TObject);
var
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  case cboOkxLimitSide.itemIndex of
    0:
      OKX.PlaceLimitOrder(okxosBuy, txtOkxInstId.Text,
        StrToFloat(txtOkxLimitSize.Text, vFS),
        StrToFloat(txtOkxLimitSize.Text, vFS));
    1:
      OKX.PlaceLimitOrder(okxosSell, txtOkxInstId.Text,
        StrToFloat(txtOkxLimitSize.Text, vFS),
        StrToFloat(txtOkxLimitSize.Text, vFS));
  end;
end;


procedure TfrmWebSocketClient.chkOkxIsDemoClick(Sender: TObject);
begin
  OKX.OKX.IsDemo := chkOkxIsDemo.Checked;
  DoServerOKX;
end;


procedure TfrmWebSocketClient.chkOkxIsPrivateClick(Sender: TObject);
begin
  OKX.OKX.IsPrivate := chkOkxIsPrivate.Checked;
  DoServerOKX;
end;


procedure TfrmWebSocketClient.DoServerOKX;
begin
  DoClear;
  OKX.Client := WSClient;

  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
  chkTLS.Checked := WSClient.TLS;
  chkOverWebSocket.Checked := WSClient.Specifications.RFC6455;

  txtOkxInstId.Text := 'BTC-USDT';
end;


procedure TfrmWebSocketClient.FormClose(Sender: TObject;
  var Action: TCloseAction);
begin
  WSClient.Active := False;
end;


procedure TfrmWebSocketClient.OKXConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.OKXDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.OKXOKXConnect(Sender: TObject;
  aMessage, aCode, aRawMessage: string);
begin
  DoLog('#connected OKX');
end;


procedure TfrmWebSocketClient.OKXOKXError(Sender: TObject;
  aCode, aMessage, aRawMessage: string);
begin
  DoLog('#error: ' + aMessage);
end;


procedure TfrmWebSocketClient.OKXOKXMessage(Sender: TObject;
  aType, aRawMessage: string);
begin
  DoLog(aRawMessage);
end;


procedure TfrmWebSocketClient.OKXOKXSubscribed(Sender: TObject;
  aChannel, aInstId, aRawMessage: string);
begin
  DoLog('#subscribed: ' + aChannel + ' ' + aInstId);
end;


procedure TfrmWebSocketClient.OKXOKXUnsubscribed(Sender: TObject;
  aChannel, aInstId, aRawMessage: string);
begin
  DoLog('#unsubscribed: ' + aChannel + ' ' + aInstId);
end;


procedure TfrmWebSocketClient.tabOKXShow(Sender: TObject);
begin
  DoServerOKX;
end;


procedure TfrmWebSocketClient.txtOkxApiKeyChange(Sender: TObject);
begin
  OKX.OKX.ApiKey := txtOkxApiKey.Text;
end;


procedure TfrmWebSocketClient.txtOkxApiSecretChange(Sender: TObject);
begin
  OKX.OKX.ApiSecret := txtOkxApiSecret.Text;
end;


procedure TfrmWebSocketClient.txtOkxPassphraseChange(Sender: TObject);
begin
  OKX.OKX.Passphrase := txtOkxPassphrase.Text;
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
  OKX.Client := nil;
end;

procedure TfrmWebSocketClient.DoBeforeConnect;
begin
end;

procedure TfrmWebSocketClient.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
end;


procedure TfrmWebSocketClient.btnOKXSubscribeAllTradesClick(Sender: TObject);
begin
  OKX.SubscribeAllTrades(txtOkxInstId.Text);
end;


procedure TfrmWebSocketClient.btnOKXUnSubscribeAllTradesClick(Sender: TObject);
begin
  OKX.UnSubscribeAllTrades(txtOkxInstId.Text);
end;


procedure TfrmWebSocketClient.btnOKXSubscribeFillsClick(Sender: TObject);
begin
  OKX.SubscribeFills;
end;


procedure TfrmWebSocketClient.btnOKXUnSubscribeFillsClick(Sender: TObject);
begin
  OKX.UnSubscribeFills;
end;


procedure TfrmWebSocketClient.btnOKXBatchPlaceOrdersClick(Sender: TObject);
begin
  DoLog('#BatchPlaceOrders placeholder - requires order JSON configuration');
end;

end.
```

