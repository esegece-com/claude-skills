# TsgcWSAPI_Deribit - Example

Full source of `uDeribit.pas` from the **05.Crypto/18.Deribit** demo, which uses `TsgcWSAPI_Deribit`.

API reference: [TsgcWSAPI_Deribit](../reference/api/TsgcWSAPI_Deribit.md)
Source demo: `05.Crypto/18.Deribit` (file `uDeribit.pas`)

```pascal
unit uDeribit;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_Deribit, sgcHTTP_API_Deribit;

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
    Deribit: TsgcWSAPI_Deribit;
    tabDeribit: TTabSheet;
    Panel9: TPanel;
    Label45: TLabel;
    Label46: TLabel;
    Label84: TLabel;
    txtDeribitClientId: TEdit;
    txtDeribitInstrument: TEdit;
    txtDeribitClientSecret: TEdit;
    chkDeribitTestNet: TCheckBox;
    PageControl8: TPageControl;
    tabDeribitWebSocket: TTabSheet;
    GroupBox15: TGroupBox;
    btnDeribitSubscribeTicker: TButton;
    btnDeribitUnSubscribeTicker: TButton;
    btnDeribitSubscribeTrades: TButton;
    btnDeribitUnSubscribeTrades: TButton;
    btnDeribitSubscribeOrderBook: TButton;
    btnDeribitUnSubscribeOrderBook: TButton;
    btnDeribitSubscribeCandle: TButton;
    btnDeribitUnSubscribeCandle: TButton;
    btnDeribitSubscribePerpetual: TButton;
    btnDeribitUnSubscribePerpetual: TButton;
    btnDeribitSubscribeOrders: TButton;
    btnDeribitUnSubscribeOrders: TButton;
    btnDeribitSubscribePositions: TButton;
    btnDeribitUnSubscribePositions: TButton;
    btnDeribitPing: TButton;
    tabDeribitRESTApi: TTabSheet;
    GroupBox19: TGroupBox;
    btnDeribitRESTAuthenticate: TButton;
    btnDeribitRESTGetInstruments: TButton;
    btnDeribitRESTGetTicker: TButton;
    btnDeribitRESTGetOrderBook: TButton;
    btnDeribitRESTGetTrades: TButton;
    btnDeribitRESTGetAccountSummary: TButton;
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure DeribitConnect(Connection: TsgcWSConnection);
    procedure DeribitDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure DeribitDeribitAuthentication(Sender: TObject; aSuccess: Boolean;
      const aError, aRawMessage: string);
    procedure DeribitDeribitSubscribe(Sender: TObject; const aRequestId: Integer;
      aSuccess: Boolean; const aError, aRawMessage: string);
    procedure DeribitDeribitUnSubscribe(Sender: TObject; const aRequestId: Integer;
      aSuccess: Boolean; const aError, aRawMessage: string);
    procedure DeribitDeribitData(Sender: TObject; const aData: string);
    procedure DeribitDeribitError(Sender: TObject; aErrorCode: Integer;
      const aErrorMessage, aRawMessage: string);
    procedure btnDeribitSubscribeTickerClick(Sender: TObject);
    procedure btnDeribitUnSubscribeTickerClick(Sender: TObject);
    procedure btnDeribitSubscribeTradesClick(Sender: TObject);
    procedure btnDeribitUnSubscribeTradesClick(Sender: TObject);
    procedure btnDeribitSubscribeOrderBookClick(Sender: TObject);
    procedure btnDeribitUnSubscribeOrderBookClick(Sender: TObject);
    procedure btnDeribitSubscribeCandleClick(Sender: TObject);
    procedure btnDeribitUnSubscribeCandleClick(Sender: TObject);
    procedure btnDeribitSubscribePerpetualClick(Sender: TObject);
    procedure btnDeribitUnSubscribePerpetualClick(Sender: TObject);
    procedure btnDeribitSubscribeOrdersClick(Sender: TObject);
    procedure btnDeribitUnSubscribeOrdersClick(Sender: TObject);
    procedure btnDeribitSubscribePositionsClick(Sender: TObject);
    procedure btnDeribitUnSubscribePositionsClick(Sender: TObject);
    procedure btnDeribitPingClick(Sender: TObject);
    procedure btnDeribitRESTAuthenticateClick(Sender: TObject);
    procedure btnDeribitRESTGetInstrumentsClick(Sender: TObject);
    procedure btnDeribitRESTGetTickerClick(Sender: TObject);
    procedure btnDeribitRESTGetOrderBookClick(Sender: TObject);
    procedure btnDeribitRESTGetTradesClick(Sender: TObject);
    procedure btnDeribitRESTGetAccountSummaryClick(Sender: TObject);
    procedure chkDeribitTestNetClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure txtDeribitClientIdChange(Sender: TObject);
    procedure txtDeribitClientSecretChange(Sender: TObject);
    procedure tabDeribitWebSocketShow(Sender: TObject);
    procedure tabDeribitRESTApiShow(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServerDeribit;
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
  Deribit.Client := WSClient;

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


procedure TfrmWebSocketClient.btnDeribitSubscribeTickerClick(Sender: TObject);
begin
  Deribit.SubscribeTicker(txtDeribitInstrument.Text);
end;


procedure TfrmWebSocketClient.btnDeribitUnSubscribeTickerClick(Sender: TObject);
begin
  Deribit.UnSubscribeTicker(txtDeribitInstrument.Text);
end;


procedure TfrmWebSocketClient.btnDeribitSubscribeTradesClick(Sender: TObject);
begin
  Deribit.SubscribeTrades(txtDeribitInstrument.Text);
end;


procedure TfrmWebSocketClient.btnDeribitUnSubscribeTradesClick(Sender: TObject);
begin
  Deribit.UnSubscribeTrades(txtDeribitInstrument.Text);
end;


procedure TfrmWebSocketClient.btnDeribitSubscribeOrderBookClick(Sender: TObject);
begin
  Deribit.SubscribeOrderBook(txtDeribitInstrument.Text);
end;


procedure TfrmWebSocketClient.btnDeribitUnSubscribeOrderBookClick
  (Sender: TObject);
begin
  Deribit.UnSubscribeOrderBook(txtDeribitInstrument.Text);
end;


procedure TfrmWebSocketClient.btnDeribitSubscribeCandleClick(Sender: TObject);
begin
  Deribit.SubscribeCandle(txtDeribitInstrument.Text);
end;


procedure TfrmWebSocketClient.btnDeribitUnSubscribeCandleClick(Sender: TObject);
begin
  Deribit.UnSubscribeCandle(txtDeribitInstrument.Text);
end;


procedure TfrmWebSocketClient.btnDeribitSubscribePerpetualClick(Sender: TObject);
begin
  Deribit.SubscribePerpetual(txtDeribitInstrument.Text);
end;


procedure TfrmWebSocketClient.btnDeribitUnSubscribePerpetualClick
  (Sender: TObject);
begin
  Deribit.UnSubscribePerpetual(txtDeribitInstrument.Text);
end;


procedure TfrmWebSocketClient.btnDeribitSubscribeOrdersClick(Sender: TObject);
begin
  Deribit.SubscribeOrders(txtDeribitInstrument.Text);
end;


procedure TfrmWebSocketClient.btnDeribitUnSubscribeOrdersClick(Sender: TObject);
begin
  Deribit.UnSubscribeOrders(txtDeribitInstrument.Text);
end;


procedure TfrmWebSocketClient.btnDeribitSubscribePositionsClick(Sender: TObject);
begin
  Deribit.SubscribePositions('BTC');
end;


procedure TfrmWebSocketClient.btnDeribitUnSubscribePositionsClick
  (Sender: TObject);
begin
  Deribit.UnSubscribePositions('BTC');
end;


procedure TfrmWebSocketClient.btnDeribitPingClick(Sender: TObject);
begin
  Deribit.Ping;
end;


procedure TfrmWebSocketClient.btnDeribitRESTAuthenticateClick(Sender: TObject);
begin
  DoLog(Deribit.REST_API.Authenticate);
end;


procedure TfrmWebSocketClient.btnDeribitRESTGetInstrumentsClick(Sender: TObject);
begin
  DoLog(Deribit.REST_API.GetInstruments('BTC'));
end;


procedure TfrmWebSocketClient.btnDeribitRESTGetTickerClick(Sender: TObject);
begin
  DoLog(Deribit.REST_API.GetTicker(txtDeribitInstrument.Text));
end;


procedure TfrmWebSocketClient.btnDeribitRESTGetOrderBookClick(Sender: TObject);
begin
  DoLog(Deribit.REST_API.GetOrderBook(txtDeribitInstrument.Text));
end;


procedure TfrmWebSocketClient.btnDeribitRESTGetTradesClick(Sender: TObject);
begin
  DoLog(Deribit.REST_API.GetTrades(txtDeribitInstrument.Text));
end;


procedure TfrmWebSocketClient.btnDeribitRESTGetAccountSummaryClick
  (Sender: TObject);
begin
  DoLog(Deribit.REST_API.GetAccountSummary('BTC'));
end;


procedure TfrmWebSocketClient.DeribitConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.DeribitDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.DeribitDeribitAuthentication(Sender: TObject;
  aSuccess: Boolean; const aError, aRawMessage: string);
begin
  if aSuccess then
    DoLog('#Deribit Authenticated')
  else
    DoLog('#Deribit Authenticated error: ' + aError);
end;


procedure TfrmWebSocketClient.DeribitDeribitSubscribe(Sender: TObject;
  const aRequestId: Integer; aSuccess: Boolean;
  const aError, aRawMessage: string);
begin
  if aSuccess then
    DoLog('#Deribit subscribe ok ' + IntToStr(aRequestId))
  else
    DoLog('#Deribit subscribe error ' + aError);
end;


procedure TfrmWebSocketClient.DeribitDeribitUnSubscribe(Sender: TObject;
  const aRequestId: Integer; aSuccess: Boolean;
  const aError, aRawMessage: string);
begin
  if aSuccess then
    DoLog('#Deribit unsubscribe ok ' + IntToStr(aRequestId))
  else
    DoLog('#Deribit unsubscribe error ' + aError);
end;


procedure TfrmWebSocketClient.DeribitDeribitData(Sender: TObject;
  const aData: string);
begin
  DoLog(aData);
end;


procedure TfrmWebSocketClient.DeribitDeribitError(Sender: TObject;
  aErrorCode: Integer; const aErrorMessage, aRawMessage: string);
begin
  DoLog('#Deribit Error: ' + aErrorMessage);
end;


procedure TfrmWebSocketClient.chkDeribitTestNetClick(Sender: TObject);
begin
  Deribit.Deribit.TestNet := chkDeribitTestNet.Checked;

  DoServerDeribit;
end;


procedure TfrmWebSocketClient.DoServerDeribit;
begin
  DoClear;
  Deribit.Client := WSClient;

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


procedure TfrmWebSocketClient.tabDeribitWebSocketShow(Sender: TObject);
begin
  DoServerDeribit;
end;


procedure TfrmWebSocketClient.tabDeribitRESTApiShow(Sender: TObject);
begin
  DoServerDeribit;
end;


procedure TfrmWebSocketClient.txtDeribitClientIdChange(Sender: TObject);
begin
  Deribit.Deribit.ApiKey := txtDeribitClientId.Text;
  DoServerDeribit;
end;


procedure TfrmWebSocketClient.txtDeribitClientSecretChange(Sender: TObject);
begin
  Deribit.Deribit.ApiSecret := txtDeribitClientSecret.Text;
  DoServerDeribit;
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
  Deribit.Client := nil;
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

