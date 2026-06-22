# TsgcWSAPI_Cex - Example

Full source of `uCex.pas` from the **05.Crypto/04.Cex** demo, which uses `TsgcWSAPI_Cex`.

API reference: [TsgcWSAPI_Cex](../reference/api/TsgcWSAPI_Cex.md)
Source demo: `05.Crypto/04.Cex` (file `uCex.pas`)

```pascal
unit uCex;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_Cex;

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
    tabCEX: TTabSheet;
    CEX: TsgcWSAPI_Cex;
    btnCexSubscribeTickers: TButton;
    Label31: TLabel;
    Label32: TLabel;
    txtCexApiSecret: TEdit;
    txtCexApiKey: TEdit;
    btnCexAuthenticate: TButton;
    btnCexUnSubscribeTickers: TButton;
    Label33: TLabel;
    txtCexSymbol1: TEdit;
    txtCexSymbol2: TEdit;
    btnCexSubscribeCharts: TButton;
    cboCexPeriods: TComboBox;
    btnCexGetTicker: TButton;
    btnCexGetBalance: TButton;
    btnCexSubscribeOrderBook: TButton;
    btnCexUnsubscribeOrderBook: TButton;
    btnCexGetOpenOrders: TButton;
    btnCexGetArchivedOrders: TButton;
    btnCexGetOpenPositions: TButton;
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnCexSubscribeTickersClick(Sender: TObject);
    procedure btnCexAuthenticateClick(Sender: TObject);
    procedure btnCexGetBalanceClick(Sender: TObject);
    procedure btnCexGetTickerClick(Sender: TObject);
    procedure btnCexSubscribeChartsClick(Sender: TObject);
    procedure btnCexSubscribeOrderBookClick(Sender: TObject);
    procedure btnCexUnsubscribeOrderBookClick(Sender: TObject);
    procedure btnCexUnSubscribeTickersClick(Sender: TObject);
    procedure btnCexGetOpenOrdersClick(Sender: TObject);
    procedure btnCexGetArchivedOrdersClick(Sender: TObject);
    procedure btnCexGetOpenPositionsClick(Sender: TObject);
    procedure CEXCexAuthenticated(Sender: TObject);
    procedure CEXCexConnect(Sender: TObject);
    procedure CEXCexDisconnect(Sender: TObject);
    procedure CEXCexDisconnecting(Sender: TObject; Reason, Time: string);
    procedure CEXCexError(Sender: TObject; Error: string);
    procedure CEXCexMessage(Sender: TObject; Event, Msg: string);
    procedure CEXCexSubscribed(Sender: TObject; Channel: string);
    procedure CEXDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure tabCEXShow(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServerCEX;
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


procedure TfrmWebSocketClient.btnCexSubscribeTickersClick(Sender: TObject);
begin
  CEX.SubscribeTickers;
end;


procedure TfrmWebSocketClient.btnCexAuthenticateClick(Sender: TObject);
begin
  CEX.Cex.ApiKey := txtCexApiKey.Text;
  CEX.Cex.ApiSecret := txtCexApiSecret.Text;
  CEX.Authenticate;
end;


procedure TfrmWebSocketClient.btnCexGetBalanceClick(Sender: TObject);
begin
  CEX.GetBalance;
end;


procedure TfrmWebSocketClient.btnCexGetTickerClick(Sender: TObject);
begin
  CEX.GetTicker(txtCexSymbol1.Text, txtCexSymbol2.Text);
end;


procedure TfrmWebSocketClient.btnCexSubscribeChartsClick(Sender: TObject);
begin
  CEX.SubscribeChart(TsgcWSCexPeriods(cboCexPeriods.itemIndex),
    txtCexSymbol1.Text, txtCexSymbol2.Text);
end;


procedure TfrmWebSocketClient.btnCexSubscribeOrderBookClick(Sender: TObject);
begin
  CEX.SubscribeOrderBook(txtCexSymbol1.Text, txtCexSymbol2.Text);
end;


procedure TfrmWebSocketClient.btnCexUnsubscribeOrderBookClick(Sender: TObject);
begin
  CEX.UnSubscribeOrderBook(txtCexSymbol1.Text, txtCexSymbol2.Text);
end;


procedure TfrmWebSocketClient.btnCexUnSubscribeTickersClick(Sender: TObject);
begin
  CEX.UnSubscribeTickers;
end;


procedure TfrmWebSocketClient.btnCexGetOpenOrdersClick(Sender: TObject);
begin
  CEX.GetOpenOrders(txtCexSymbol1.Text, txtCexSymbol2.Text);
end;


procedure TfrmWebSocketClient.btnCexGetArchivedOrdersClick(Sender: TObject);
begin
  CEX.GetArchivedOrders(txtCexSymbol1.Text, txtCexSymbol2.Text);
end;


procedure TfrmWebSocketClient.btnCexGetOpenPositionsClick(Sender: TObject);
begin
  CEX.GetOpenPositions(txtCexSymbol1.Text, txtCexSymbol2.Text);
end;


procedure TfrmWebSocketClient.CEXCexAuthenticated(Sender: TObject);
begin
  DoLog('#authenticated');
end;


procedure TfrmWebSocketClient.CEXCexConnect(Sender: TObject);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.CEXCexDisconnect(Sender: TObject);
begin
  DoLog('#disconnected from CEX');
end;


procedure TfrmWebSocketClient.CEXCexDisconnecting(Sender: TObject;
  Reason, Time: string);
begin
  DoLog('#disconnecting from CEX: ' + Reason);
end;


procedure TfrmWebSocketClient.CEXCexError(Sender: TObject; Error: string);
begin
  DoLog('#error: ' + Error);
end;


procedure TfrmWebSocketClient.CEXCexMessage(Sender: TObject;
  Event, Msg: string);
begin
  DoLog(Msg);
end;


procedure TfrmWebSocketClient.CEXCexSubscribed(Sender: TObject;
  Channel: string);
begin
  DoLog('#subscribed: ' + Channel);
end;


procedure TfrmWebSocketClient.CEXDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.DoServerCEX;
begin
  DoClear;
  CEX.Client := WSClient;

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


procedure TfrmWebSocketClient.tabCEXShow(Sender: TObject);
begin
  DoServerCEX;
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
  CEX.Client := nil;
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

