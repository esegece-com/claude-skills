# TsgcWSAPI_CryptoCom - Example

Full source of `uCryptoCom.pas` from the **05.Crypto/19.CryptoCom** demo, which uses `TsgcWSAPI_CryptoCom`.

API reference: [TsgcWSAPI_CryptoCom](../reference/api/TsgcWSAPI_CryptoCom.md)
Source demo: `05.Crypto/19.CryptoCom` (file `uCryptoCom.pas`)

```pascal
unit uCryptoCom;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_CryptoCom, sgcHTTP_API_CryptoCom;

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
    CryptoCom: TsgcWSAPI_CryptoCom;
    tabCryptoCom: TTabSheet;
    Panel9: TPanel;
    Label45: TLabel;
    Label46: TLabel;
    Label84: TLabel;
    txtCryptoComAPIKey: TEdit;
    txtCryptoComInstrument: TEdit;
    txtCryptoComAPISecret: TEdit;
    PageControl8: TPageControl;
    tabCryptoComWebSocket: TTabSheet;
    GroupBox15: TGroupBox;
    btnCryptoComSubscribeTicker: TButton;
    btnCryptoComUnSubscribeTicker: TButton;
    btnCryptoComSubscribeTrade: TButton;
    btnCryptoComUnSubscribeTrade: TButton;
    btnCryptoComSubscribeCandlestick: TButton;
    btnCryptoComUnSubscribeCandlestick: TButton;
    btnCryptoComSubscribeBook: TButton;
    btnCryptoComUnSubscribeBook: TButton;
    btnCryptoComSubscribeOrders: TButton;
    btnCryptoComUnSubscribeOrders: TButton;
    btnCryptoComSubscribeUserTrades: TButton;
    btnCryptoComUnSubscribeUserTrades: TButton;
    btnCryptoComSubscribeBalance: TButton;
    btnCryptoComUnSubscribeBalance: TButton;
    btnCryptoComPing: TButton;
    btnCryptoComInitialize: TButton;
    tabCryptoComRESTApi: TTabSheet;
    GroupBox19: TGroupBox;
    btnCryptoComRESTGetInstruments: TButton;
    btnCryptoComRESTGetTicker: TButton;
    btnCryptoComRESTOrderBook: TButton;
    btnCryptoComRESTGetTrades: TButton;
    btnCryptoComRESTGetAccountSummary: TButton;
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnCryptoComSubscribeTickerClick(Sender: TObject);
    procedure btnCryptoComUnSubscribeTickerClick(Sender: TObject);
    procedure btnCryptoComSubscribeTradeClick(Sender: TObject);
    procedure btnCryptoComUnSubscribeTradeClick(Sender: TObject);
    procedure btnCryptoComSubscribeCandlestickClick(Sender: TObject);
    procedure btnCryptoComUnSubscribeCandlestickClick(Sender: TObject);
    procedure btnCryptoComSubscribeBookClick(Sender: TObject);
    procedure btnCryptoComUnSubscribeBookClick(Sender: TObject);
    procedure btnCryptoComSubscribeOrdersClick(Sender: TObject);
    procedure btnCryptoComUnSubscribeOrdersClick(Sender: TObject);
    procedure btnCryptoComSubscribeUserTradesClick(Sender: TObject);
    procedure btnCryptoComUnSubscribeUserTradesClick(Sender: TObject);
    procedure btnCryptoComSubscribeBalanceClick(Sender: TObject);
    procedure btnCryptoComUnSubscribeBalanceClick(Sender: TObject);
    procedure btnCryptoComPingClick(Sender: TObject);
    procedure btnCryptoComInitializeClick(Sender: TObject);
    procedure btnCryptoComRESTGetInstrumentsClick(Sender: TObject);
    procedure btnCryptoComRESTGetTickerClick(Sender: TObject);
    procedure btnCryptoComRESTOrderBookClick(Sender: TObject);
    procedure btnCryptoComRESTGetTradesClick(Sender: TObject);
    procedure btnCryptoComRESTGetAccountSummaryClick(Sender: TObject);
    procedure CryptoComConnect(Connection: TsgcWSConnection);
    procedure CryptoComDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure CryptoComCryptoComAuthentication(Sender: TObject;
      aSuccess: Boolean; const aError, aRawMessage: string);
    procedure CryptoComCryptoComSubscribe(Sender: TObject;
      const aId: Integer; const aRawMessage: string);
    procedure CryptoComCryptoComUnSubscribe(Sender: TObject;
      const aId: Integer; const aRawMessage: string);
    procedure CryptoComCryptoComData(Sender: TObject; const aData: string);
    procedure CryptoComCryptoComError(Sender: TObject;
      aErrorCode: Integer; const aErrorMessage, aRawMessage: string);
    procedure txtCryptoComAPIKeyChange(Sender: TObject);
    procedure txtCryptoComAPISecretChange(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure tabCryptoComWebSocketShow(Sender: TObject);
    procedure tabCryptoComRESTApiShow(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServerCryptoCom;
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
  CryptoCom.Client := WSClient;

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


procedure TfrmWebSocketClient.btnCryptoComSubscribeTickerClick(Sender: TObject);
begin
  CryptoCom.SubscribeTicker(txtCryptoComInstrument.Text);
end;


procedure TfrmWebSocketClient.btnCryptoComUnSubscribeTickerClick(Sender: TObject);
begin
  CryptoCom.UnSubscribeTicker(txtCryptoComInstrument.Text);
end;


procedure TfrmWebSocketClient.btnCryptoComSubscribeTradeClick(Sender: TObject);
begin
  CryptoCom.SubscribeTrade(txtCryptoComInstrument.Text);
end;


procedure TfrmWebSocketClient.btnCryptoComUnSubscribeTradeClick(Sender: TObject);
begin
  CryptoCom.UnSubscribeTrade(txtCryptoComInstrument.Text);
end;


procedure TfrmWebSocketClient.btnCryptoComSubscribeCandlestickClick(Sender: TObject);
begin
  CryptoCom.SubscribeCandlestick(txtCryptoComInstrument.Text);
end;


procedure TfrmWebSocketClient.btnCryptoComUnSubscribeCandlestickClick(Sender: TObject);
begin
  CryptoCom.UnSubscribeCandlestick(txtCryptoComInstrument.Text);
end;


procedure TfrmWebSocketClient.btnCryptoComSubscribeBookClick(Sender: TObject);
begin
  CryptoCom.SubscribeBook(txtCryptoComInstrument.Text);
end;


procedure TfrmWebSocketClient.btnCryptoComUnSubscribeBookClick(Sender: TObject);
begin
  CryptoCom.UnSubscribeBook(txtCryptoComInstrument.Text);
end;


procedure TfrmWebSocketClient.btnCryptoComSubscribeOrdersClick(Sender: TObject);
begin
  CryptoCom.SubscribeOrders(txtCryptoComInstrument.Text);
end;


procedure TfrmWebSocketClient.btnCryptoComUnSubscribeOrdersClick(Sender: TObject);
begin
  CryptoCom.UnSubscribeOrders(txtCryptoComInstrument.Text);
end;


procedure TfrmWebSocketClient.btnCryptoComSubscribeUserTradesClick(Sender: TObject);
begin
  CryptoCom.SubscribeUserTrades(txtCryptoComInstrument.Text);
end;


procedure TfrmWebSocketClient.btnCryptoComUnSubscribeUserTradesClick(Sender: TObject);
begin
  CryptoCom.UnSubscribeUserTrades(txtCryptoComInstrument.Text);
end;


procedure TfrmWebSocketClient.btnCryptoComSubscribeBalanceClick(Sender: TObject);
begin
  CryptoCom.SubscribeBalance;
end;


procedure TfrmWebSocketClient.btnCryptoComUnSubscribeBalanceClick(Sender: TObject);
begin
  CryptoCom.UnSubscribeBalance;
end;


procedure TfrmWebSocketClient.btnCryptoComPingClick(Sender: TObject);
begin
  CryptoCom.Ping;
end;


procedure TfrmWebSocketClient.btnCryptoComInitializeClick(Sender: TObject);
begin
  CryptoCom.Initialize;
end;


procedure TfrmWebSocketClient.btnCryptoComRESTGetInstrumentsClick(Sender: TObject);
begin
  DoLog(CryptoCom.REST_API.GetInstruments);
end;


procedure TfrmWebSocketClient.btnCryptoComRESTGetTickerClick(Sender: TObject);
begin
  DoLog(CryptoCom.REST_API.GetTicker(txtCryptoComInstrument.Text));
end;


procedure TfrmWebSocketClient.btnCryptoComRESTOrderBookClick(Sender: TObject);
begin
  DoLog(CryptoCom.REST_API.GetOrderBook(txtCryptoComInstrument.Text));
end;


procedure TfrmWebSocketClient.btnCryptoComRESTGetTradesClick(Sender: TObject);
begin
  DoLog(CryptoCom.REST_API.GetTrades(txtCryptoComInstrument.Text));
end;


procedure TfrmWebSocketClient.btnCryptoComRESTGetAccountSummaryClick(Sender: TObject);
begin
  DoLog(CryptoCom.REST_API.GetAccountSummary);
end;


procedure TfrmWebSocketClient.CryptoComConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.CryptoComDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.CryptoComCryptoComAuthentication(Sender: TObject;
  aSuccess: Boolean; const aError, aRawMessage: string);
begin
  if aSuccess then
    DoLog('#CryptoCom Authenticated')
  else
    DoLog('#CryptoCom Authenticated error: ' + aError);
end;


procedure TfrmWebSocketClient.CryptoComCryptoComSubscribe(Sender: TObject;
  const aId: Integer; const aRawMessage: string);
begin
  DoLog('#CryptoCom subscribe ok ' + IntToStr(aId));
end;


procedure TfrmWebSocketClient.CryptoComCryptoComUnSubscribe(Sender: TObject;
  const aId: Integer; const aRawMessage: string);
begin
  DoLog('#CryptoCom unsubscribe ok ' + IntToStr(aId));
end;


procedure TfrmWebSocketClient.CryptoComCryptoComData(Sender: TObject;
  const aData: string);
begin
  DoLog(aData);
end;


procedure TfrmWebSocketClient.CryptoComCryptoComError(Sender: TObject;
  aErrorCode: Integer; const aErrorMessage, aRawMessage: string);
begin
  DoLog('#CryptoCom Error: ' + aErrorMessage);
end;


procedure TfrmWebSocketClient.txtCryptoComAPIKeyChange(Sender: TObject);
begin
  CryptoCom.CryptoCom.ApiKey := txtCryptoComAPIKey.Text;
  DoServerCryptoCom;
end;


procedure TfrmWebSocketClient.txtCryptoComAPISecretChange(Sender: TObject);
begin
  CryptoCom.CryptoCom.ApiSecret := txtCryptoComAPISecret.Text;
  DoServerCryptoCom;
end;


procedure TfrmWebSocketClient.DoServerCryptoCom;
begin
  DoClear;
  CryptoCom.Client := WSClient;

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


procedure TfrmWebSocketClient.tabCryptoComWebSocketShow(Sender: TObject);
begin
  DoServerCryptoCom;
end;


procedure TfrmWebSocketClient.tabCryptoComRESTApiShow(Sender: TObject);
begin
  DoServerCryptoCom;
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
  CryptoCom.Client := nil;
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

