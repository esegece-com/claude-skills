# TsgcWSAPI_GateIO - Example

Full source of `uGateIO.pas` from the **05.Crypto/17.GateIO** demo, which uses `TsgcWSAPI_GateIO`.

API reference: [TsgcWSAPI_GateIO](../reference/api/TsgcWSAPI_GateIO.md)
Source demo: `05.Crypto/17.GateIO` (file `uGateIO.pas`)

```pascal
unit uGateIO;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_GateIO, sgcHTTP_API_GateIO;

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
    GateIO: TsgcWSAPI_GateIO;
    tabGateIO: TTabSheet;
    Panel9: TPanel;
    Label45: TLabel;
    Label46: TLabel;
    Label84: TLabel;
    txtGateIOAPIKey: TEdit;
    txtGateIOSymbol: TEdit;
    txtGateIOAPISecret: TEdit;
    PageControl8: TPageControl;
    tabGateIOWebSocket: TTabSheet;
    GroupBox15: TGroupBox;
    btnGateIOSubscribeTicker: TButton;
    btnGateIOUnSubscribeTicker: TButton;
    btnGateIOSubscribeTrades: TButton;
    btnGateIOUnSubscribeTrades: TButton;
    btnGateIOSubscribeCandlesticks: TButton;
    btnGateIOUnSubscribeCandlesticks: TButton;
    btnGateIOSubscribeOrderBook: TButton;
    btnGateIOUnSubscribeOrderBook: TButton;
    btnGateIOSubscribeOrders: TButton;
    btnGateIOUnSubscribeOrders: TButton;
    btnGateIOSubscribeBalances: TButton;
    btnGateIOUnSubscribeBalances: TButton;
    btnGateIOPing: TButton;
    tabGateIORESTApi: TTabSheet;
    GroupBox19: TGroupBox;
    btnGateIORESTCurrencyPairs: TButton;
    btnGateIORESTTickers: TButton;
    btnGateIORESTOrderBook: TButton;
    btnGateIORESTTrades: TButton;
    btnGateIORESTSpotAccounts: TButton;
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure GateIOConnect(Connection: TsgcWSConnection);
    procedure GateIODisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure GateIOGateIOAuthentication(Sender: TObject; aSuccess: Boolean;
      const aError, aRawMessage: string);
    procedure GateIOGateIOSubscribe(Sender: TObject; const aChannel: string;
      aSuccess: Boolean; const aError, aRawMessage: string);
    procedure GateIOGateIOUnSubscribe(Sender: TObject; const aChannel: string;
      aSuccess: Boolean; const aError, aRawMessage: string);
    procedure GateIOGateIOData(Sender: TObject; const aData: string);
    procedure GateIOGateIOError(Sender: TObject; aErrorCode: string;
      const aErrorMessage, aRawMessage: string);
    procedure btnGateIOSubscribeTickerClick(Sender: TObject);
    procedure btnGateIOUnSubscribeTickerClick(Sender: TObject);
    procedure btnGateIOSubscribeTradesClick(Sender: TObject);
    procedure btnGateIOUnSubscribeTradesClick(Sender: TObject);
    procedure btnGateIOSubscribeCandlesticksClick(Sender: TObject);
    procedure btnGateIOUnSubscribeCandlesticksClick(Sender: TObject);
    procedure btnGateIOSubscribeOrderBookClick(Sender: TObject);
    procedure btnGateIOUnSubscribeOrderBookClick(Sender: TObject);
    procedure btnGateIOSubscribeOrdersClick(Sender: TObject);
    procedure btnGateIOUnSubscribeOrdersClick(Sender: TObject);
    procedure btnGateIOSubscribeBalancesClick(Sender: TObject);
    procedure btnGateIOUnSubscribeBalancesClick(Sender: TObject);
    procedure btnGateIOPingClick(Sender: TObject);
    procedure btnGateIORESTCurrencyPairsClick(Sender: TObject);
    procedure btnGateIORESTTickersClick(Sender: TObject);
    procedure btnGateIORESTOrderBookClick(Sender: TObject);
    procedure btnGateIORESTTradesClick(Sender: TObject);
    procedure btnGateIORESTSpotAccountsClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure txtGateIOAPIKeyChange(Sender: TObject);
    procedure txtGateIOAPISecretChange(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  end;

var
  frmWebSocketClient: TfrmWebSocketClient;

implementation

uses
  sgcWebSocket_Helpers, sgcJSON, StrUtils, sgcBase_Helpers,
  ShellAPI, DateUtils;
{$R *.dfm}

procedure TfrmWebSocketClient.FormCreate(Sender: TObject);
begin
  GateIO.Client := WSClient;

  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
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


procedure TfrmWebSocketClient.btnGateIOSubscribeTickerClick(Sender: TObject);
begin
  GateIO.SubscribeTicker(txtGateIOSymbol.Text);
end;


procedure TfrmWebSocketClient.btnGateIOUnSubscribeTickerClick(Sender: TObject);
begin
  GateIO.UnSubscribeTicker(txtGateIOSymbol.Text);
end;


procedure TfrmWebSocketClient.btnGateIOSubscribeTradesClick(Sender: TObject);
begin
  GateIO.SubscribeTrades(txtGateIOSymbol.Text);
end;


procedure TfrmWebSocketClient.btnGateIOUnSubscribeTradesClick(Sender: TObject);
begin
  GateIO.UnSubscribeTrades(txtGateIOSymbol.Text);
end;


procedure TfrmWebSocketClient.btnGateIOSubscribeCandlesticksClick
  (Sender: TObject);
begin
  GateIO.SubscribeCandlesticks(txtGateIOSymbol.Text);
end;


procedure TfrmWebSocketClient.btnGateIOUnSubscribeCandlesticksClick
  (Sender: TObject);
begin
  GateIO.UnSubscribeCandlesticks(txtGateIOSymbol.Text);
end;


procedure TfrmWebSocketClient.btnGateIOSubscribeOrderBookClick
  (Sender: TObject);
begin
  GateIO.SubscribeOrderBook(txtGateIOSymbol.Text);
end;


procedure TfrmWebSocketClient.btnGateIOUnSubscribeOrderBookClick
  (Sender: TObject);
begin
  GateIO.UnSubscribeOrderBook(txtGateIOSymbol.Text);
end;


procedure TfrmWebSocketClient.btnGateIOSubscribeOrdersClick(Sender: TObject);
begin
  GateIO.SubscribeOrders(txtGateIOSymbol.Text);
end;


procedure TfrmWebSocketClient.btnGateIOUnSubscribeOrdersClick(Sender: TObject);
begin
  GateIO.UnSubscribeOrders(txtGateIOSymbol.Text);
end;


procedure TfrmWebSocketClient.btnGateIOSubscribeBalancesClick(Sender: TObject);
begin
  GateIO.SubscribeBalances;
end;


procedure TfrmWebSocketClient.btnGateIOUnSubscribeBalancesClick
  (Sender: TObject);
begin
  GateIO.UnSubscribeBalances;
end;


procedure TfrmWebSocketClient.btnGateIOPingClick(Sender: TObject);
begin
  GateIO.Ping;
end;


procedure TfrmWebSocketClient.btnGateIORESTCurrencyPairsClick(Sender: TObject);
begin
  DoLog(GateIO.REST_API.GetCurrencyPairs);
end;


procedure TfrmWebSocketClient.btnGateIORESTTickersClick(Sender: TObject);
begin
  DoLog(GateIO.REST_API.GetTickers(txtGateIOSymbol.Text));
end;


procedure TfrmWebSocketClient.btnGateIORESTOrderBookClick(Sender: TObject);
begin
  DoLog(GateIO.REST_API.GetOrderBook(txtGateIOSymbol.Text));
end;


procedure TfrmWebSocketClient.btnGateIORESTTradesClick(Sender: TObject);
begin
  DoLog(GateIO.REST_API.GetTrades(txtGateIOSymbol.Text));
end;


procedure TfrmWebSocketClient.btnGateIORESTSpotAccountsClick(Sender: TObject);
begin
  DoLog(GateIO.REST_API.GetSpotAccounts);
end;


procedure TfrmWebSocketClient.GateIOConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.GateIODisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.GateIOGateIOAuthentication(Sender: TObject;
  aSuccess: Boolean; const aError, aRawMessage: string);
begin
  if aSuccess then
    DoLog('#GateIO Authenticated')
  else
    DoLog('#GateIO Authenticated error: ' + aError);
end;


procedure TfrmWebSocketClient.GateIOGateIOSubscribe(Sender: TObject;
  const aChannel: string; aSuccess: Boolean;
  const aError, aRawMessage: string);
begin
  if aSuccess then
    DoLog('#GateIO subscribe ok ' + aChannel)
  else
    DoLog('#GateIO subscribe error ' + aError);
end;


procedure TfrmWebSocketClient.GateIOGateIOUnSubscribe(Sender: TObject;
  const aChannel: string; aSuccess: Boolean;
  const aError, aRawMessage: string);
begin
  if aSuccess then
    DoLog('#GateIO unsubscribe ok ' + aChannel)
  else
    DoLog('#GateIO unsubscribe error ' + aError);
end;


procedure TfrmWebSocketClient.GateIOGateIOData(Sender: TObject;
  const aData: string);
begin
  DoLog(aData);
end;


procedure TfrmWebSocketClient.GateIOGateIOError(Sender: TObject;
  aErrorCode: string; const aErrorMessage, aRawMessage: string);
begin
  DoLog('#GateIO Error: ' + aErrorMessage);
end;


procedure TfrmWebSocketClient.txtGateIOAPIKeyChange(Sender: TObject);
begin
  GateIO.GateIO.ApiKey := txtGateIOAPIKey.Text;
end;


procedure TfrmWebSocketClient.txtGateIOAPISecretChange(Sender: TObject);
begin
  GateIO.GateIO.ApiSecret := txtGateIOAPISecret.Text;
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


procedure TfrmWebSocketClient.FormClose(Sender: TObject;
  var Action: TCloseAction);
begin
  WSClient.Active := False;
end;


procedure TfrmWebSocketClient.DoClear;
begin
  GateIO.Client := nil;
end;

procedure TfrmWebSocketClient.DoBeforeConnect;
begin
  GateIO.Client := WSClient;
end;

procedure TfrmWebSocketClient.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
end;

end.
```

