# TsgcWSAPI_XTB - Example

Full source of `uXTB.pas` from the **05.Crypto/13.XTB** demo, which uses `TsgcWSAPI_XTB`.

API reference: [TsgcWSAPI_XTB](../reference/api/TsgcWSAPI_XTB.md)
Source demo: `05.Crypto/13.XTB` (file `uXTB.pas`)

```pascal
unit uXTB;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_XTB;

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
    tabXTB: TTabSheet;
    XTB: TsgcWSAPI_XTB;
    Panel8: TPanel;
    Label18: TLabel;
    Label26: TLabel;
    txtXTBUser: TEdit;
    txtXTBPassword: TEdit;
    chkXTBDemo: TCheckBox;
    pageXTB: TPageControl;
    tabXTBTrading: TTabSheet;
    tabXTBStreaming: TTabSheet;
    btnXTBGetAllSymbols: TButton;
    btnXTBGetCurrentUserData: TButton;
    btnXTBGetServerTime: TButton;
    btnXTBGetSymbol: TButton;
    Label24: TLabel;
    txtXTBSymbol: TEdit;
    btnXTBGetTickPrices: TButton;
    btnXTBGetTradingHours: TButton;
    btnXTBGetTrades: TButton;
    btnXTBGetVersion: TButton;
    btnXTBSubscribeBalance: TButton;
    btnXTBUnsubscribeBalance: TButton;
    btnXTBUnsubscribeCandles: TButton;
    btnXTBSubscribeCandles: TButton;
    btnSubscribeTrades: TButton;
    btnUnsubscribeTrades: TButton;
    btnXTBSubscribeTradeStatus: TButton;
    btnXTBUnsubscribeTradeStatus: TButton;
    btnXTBSubscribeTickPrices: TButton;
    btnXTBUnsubscribeTickPrices: TButton;
    Label25: TLabel;
    Label27: TLabel;
    cboXTBMarketSide: TComboBox;
    txtXTBMarketSize: TEdit;
    btnXTBMarketOrder: TButton;
    Label28: TLabel;
    Label29: TLabel;
    cboXTBLimitSide: TComboBox;
    txtXTBLimitSize: TEdit;
    Label39: TLabel;
    txtXTBLimitPrice: TEdit;
    btnXTBLimitOrder: TButton;
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnSubscribeTradesClick(Sender: TObject);
    procedure btnUnsubscribeTradesClick(Sender: TObject);
    procedure btnXTBGetAllSymbolsClick(Sender: TObject);
    procedure btnXTBGetCurrentUserDataClick(Sender: TObject);
    procedure btnXTBGetServerTimeClick(Sender: TObject);
    procedure btnXTBGetSymbolClick(Sender: TObject);
    procedure btnXTBGetTickPricesClick(Sender: TObject);
    procedure btnXTBGetTradesClick(Sender: TObject);
    procedure btnXTBGetTradingHoursClick(Sender: TObject);
    procedure btnXTBGetVersionClick(Sender: TObject);
    procedure btnXTBLimitOrderClick(Sender: TObject);
    procedure btnXTBMarketOrderClick(Sender: TObject);
    procedure btnXTBSubscribeBalanceClick(Sender: TObject);
    procedure btnXTBSubscribeCandlesClick(Sender: TObject);
    procedure btnXTBSubscribeTickPricesClick(Sender: TObject);
    procedure btnXTBSubscribeTradeStatusClick(Sender: TObject);
    procedure btnXTBUnsubscribeBalanceClick(Sender: TObject);
    procedure btnXTBUnsubscribeCandlesClick(Sender: TObject);
    procedure btnXTBUnsubscribeTickPricesClick(Sender: TObject);
    procedure btnXTBUnsubscribeTradeStatusClick(Sender: TObject);
    procedure chkXTBDemoClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure tabXTBShow(Sender: TObject);
    procedure txtXTBPasswordChange(Sender: TObject);
    procedure txtXTBUserChange(Sender: TObject);
    procedure XTBConnect(Connection: TsgcWSConnection);
    procedure XTBDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure XTBXTBConnect(Sender: TObject; const aStreamSessionId: string);
    procedure XTBXTBError(Sender: TObject; const aCode, aDescription,
      aRawMessage: string);
    procedure XTBXTBMessage(Sender: TObject; const aRawMessage: string);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServerXTB;
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


procedure TfrmWebSocketClient.btnSubscribeTradesClick(Sender: TObject);
begin
  XTB.SubscribeTrades;
end;


procedure TfrmWebSocketClient.btnUnsubscribeTradesClick(Sender: TObject);
begin
  XTB.UnSubscribeTrades;
end;


procedure TfrmWebSocketClient.btnXTBGetAllSymbolsClick(Sender: TObject);
begin
  XTB.GetAllSymbols;
end;


procedure TfrmWebSocketClient.btnXTBGetCurrentUserDataClick(Sender: TObject);
begin
  XTB.GetCurrentUserData;
end;


procedure TfrmWebSocketClient.btnXTBGetServerTimeClick(Sender: TObject);
begin
  XTB.GetServerTime;
end;


procedure TfrmWebSocketClient.btnXTBGetSymbolClick(Sender: TObject);
begin
  XTB.GetSymbol(txtXTBSymbol.Text);
end;


procedure TfrmWebSocketClient.btnXTBGetTickPricesClick(Sender: TObject);
begin
  XTB.GetTickPrices(txtXTBSymbol.Text, 0, Trunc(Now));
end;


procedure TfrmWebSocketClient.btnXTBGetTradesClick(Sender: TObject);
begin
  XTB.GetTrades;
end;


procedure TfrmWebSocketClient.btnXTBGetTradingHoursClick(Sender: TObject);
begin
  XTB.GetTradingHours(txtXTBSymbol.Text);
end;


procedure TfrmWebSocketClient.btnXTBGetVersionClick(Sender: TObject);
begin
  XTB.GetVersion;
end;


procedure TfrmWebSocketClient.btnXTBLimitOrderClick(Sender: TObject);
var
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  case cboXTBMarketSide.itemIndex of
    0:
      XTB.TradeTransaction(xtbcBuyLimit, '', IncDay(Now, 1), 0, 0,
        StrToFloat(txtXTBLimitPrice.Text, vFS), 0, txtXTBSymbol.Text, 0,
        xtbtOpen, StrToFloat(txtXTBLimitSize.Text, vFS));
    1:
      XTB.TradeTransaction(xtbcSellLimit, '', IncDay(Now, 1), 0, 0,
        StrToFloat(txtXTBLimitPrice.Text, vFS), 0, txtXTBSymbol.Text, 0,
        xtbtOpen, StrToFloat(txtXTBLimitSize.Text, vFS));
  end;
end;


procedure TfrmWebSocketClient.btnXTBMarketOrderClick(Sender: TObject);
var
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  case cboXTBMarketSide.itemIndex of
    0:
      XTB.TradeTransaction(xtbcBuy, '', IncDay(Now, 1), 0, 0,
        StrToFloat(txtXTBLimitPrice.Text, vFS), 0, txtXTBSymbol.Text, 0,
        xtbtOpen, StrToFloat(txtXTBMarketSize.Text, vFS));
    1:
      XTB.TradeTransaction(xtbcSell, '', IncDay(Now, 1), 0, 0,
        StrToFloat(txtXTBLimitPrice.Text, vFS), 0, txtXTBSymbol.Text, 0,
        xtbtOpen, StrToFloat(txtXTBMarketSize.Text, vFS));
  end;
end;


procedure TfrmWebSocketClient.btnXTBSubscribeBalanceClick(Sender: TObject);
begin
  XTB.SubscribeBalance;
end;


procedure TfrmWebSocketClient.btnXTBSubscribeCandlesClick(Sender: TObject);
begin
  XTB.SubscribeCandles(txtXTBSymbol.Text);
end;


procedure TfrmWebSocketClient.btnXTBSubscribeTickPricesClick(Sender: TObject);
begin
  XTB.SubscribeTickPrices(txtXTBSymbol.Text);
end;


procedure TfrmWebSocketClient.btnXTBSubscribeTradeStatusClick(Sender: TObject);
begin
  XTB.SubscribeTradeStatus;
end;


procedure TfrmWebSocketClient.btnXTBUnsubscribeBalanceClick(Sender: TObject);
begin
  XTB.UnSubscribeBalance;
end;


procedure TfrmWebSocketClient.btnXTBUnsubscribeCandlesClick(Sender: TObject);
begin
  XTB.UnsubscribeCandles(txtXTBSymbol.Text);
end;


procedure TfrmWebSocketClient.btnXTBUnsubscribeTickPricesClick(Sender: TObject);
begin
  XTB.UnSubscribeTickPrices(txtXTBSymbol.Text);
end;


procedure TfrmWebSocketClient.btnXTBUnsubscribeTradeStatusClick
  (Sender: TObject);
begin
  XTB.UnSubscribeTradeStatus;
end;


procedure TfrmWebSocketClient.chkXTBDemoClick(Sender: TObject);
begin
  XTB.XTB.Demo := chkXTBDemo.Checked;
  DoServerXTB;
end;


procedure TfrmWebSocketClient.DoServerXTB;
begin
  DoClear;
  XTB.Client := WSClient;

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


procedure TfrmWebSocketClient.tabXTBShow(Sender: TObject);
begin
  DoServerXTB;
end;


procedure TfrmWebSocketClient.txtXTBPasswordChange(Sender: TObject);
begin
  XTB.XTB.Password := txtXTBPassword.Text;
end;


procedure TfrmWebSocketClient.txtXTBUserChange(Sender: TObject);
begin
  XTB.XTB.User := txtXTBUser.Text;
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


procedure TfrmWebSocketClient.XTBConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.XTBDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.XTBXTBConnect(Sender: TObject;
  const aStreamSessionId: string);
begin
  DoLog('#connected XTB Broker');
end;


procedure TfrmWebSocketClient.XTBXTBError(Sender: TObject;
  const aCode, aDescription, aRawMessage: string);
begin
  DoLog('#error: [' + aCode + '] ' + aDescription);
end;


procedure TfrmWebSocketClient.XTBXTBMessage(Sender: TObject;
  const aRawMessage: string);
begin
  DoLog(aRawMessage);
end;


procedure TfrmWebSocketClient.DoClear;
begin
  XTB.Client := nil;
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

