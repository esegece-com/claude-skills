# TsgcWSAPI_CexPlus - Example

Full source of `uCexPlus.pas` from the **05.Crypto/05.CexPlus** demo, which uses `TsgcWSAPI_CexPlus`.

API reference: [TsgcWSAPI_CexPlus](../reference/api/TsgcWSAPI_CexPlus.md)
Source demo: `05.Crypto/05.CexPlus` (file `uCexPlus.pas`)

```pascal
unit uCexPlus;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_CexPlus;

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
    tabCEX_PLUS: TTabSheet;
    Label30: TLabel;
    txtCexPlusApiKey: TEdit;
    Label80: TLabel;
    txtCexPlusApiSecret: TEdit;
    CEX_PLUS: TsgcWSAPI_CexPlus;
    btnCexPlusSubscribeOrderBook: TButton;
    btnCexPlusUnSubscribeOrderBook: TButton;
    btnCexPlusGetCandles: TButton;
    cboCexPlusResolution: TComboBox;
    txtCexPlusPair: TEdit;
    Label119: TLabel;
    btnCexPlusUnSubscribeTrade: TButton;
    btnCexPlusSubscribeTrade: TButton;
    Label121: TLabel;
    Label122: TLabel;
    btnCexPlusAccountStatus: TButton;
    btnCexPlusGetOrders: TButton;
    btnCexPlusCancelAllOrders: TButton;
    btnCexPlusGetWalletBalance: TButton;
    btnCexPlusSubscribeAccountEvents: TButton;
    btnCexPlusUnSubscribeAccountEvents: TButton;
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnCexPlusAccountStatusClick(Sender: TObject);
    procedure btnCexPlusCancelAllOrdersClick(Sender: TObject);
    procedure btnCexPlusSubscribeOrderBookClick(Sender: TObject);
    procedure btnCexPlusSubscribeTradeClick(Sender: TObject);
    procedure btnCexPlusUnSubscribeOrderBookClick(Sender: TObject);
    procedure btnCexPlusUnSubscribeTradeClick(Sender: TObject);
    procedure btnCexPlusGetCandlesClick(Sender: TObject);
    procedure btnCexPlusGetOrdersClick(Sender: TObject);
    procedure btnCexPlusGetWalletBalanceClick(Sender: TObject);
    procedure btnCexPlusSubscribeAccountEventsClick(Sender: TObject);
    procedure btnCexPlusUnSubscribeAccountEventsClick(Sender: TObject);
    procedure CEX_PLUSCexPlusAuthenticated(Sender: TObject);
    procedure CEX_PLUSCexPlusConnect(Sender: TObject);
    procedure CEX_PLUSCexPlusDisconnect(Sender: TObject);
    procedure CEX_PLUSCexPlusDisconnecting(Sender: TObject;
      Reason, Time: string);
    procedure CEX_PLUSCexPlusError(Sender: TObject; Error: string);
    procedure CEX_PLUSCexPlusMessage(Sender: TObject; Event, Msg: string);
    procedure CEX_PLUSCexPlusSubscribed(Sender: TObject; Channel: string);
    procedure CEX_PLUSDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure tabCEX_PLUSShow(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure txtCexPlusApiKeyChange(Sender: TObject);
    procedure txtCexPlusApiSecretChange(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServerCEX_PLUS;
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


procedure TfrmWebSocketClient.btnCexPlusAccountStatusClick(Sender: TObject);
begin
  CEX_PLUS.GetAccountStatus;
end;


procedure TfrmWebSocketClient.btnCexPlusCancelAllOrdersClick(Sender: TObject);
begin
  CEX_PLUS.CancelAllOrders;
end;


procedure TfrmWebSocketClient.btnCexPlusSubscribeOrderBookClick
  (Sender: TObject);
begin
  CEX_PLUS.SubscribeOrderBook(txtCexPlusPair.Text);
end;


procedure TfrmWebSocketClient.btnCexPlusSubscribeTradeClick(Sender: TObject);
begin
  CEX_PLUS.SubscribeTrade(txtCexPlusPair.Text);
end;


procedure TfrmWebSocketClient.btnCexPlusUnSubscribeOrderBookClick
  (Sender: TObject);
begin
  CEX_PLUS.UnSubscribeOrderBook(txtCexPlusPair.Text);
end;


procedure TfrmWebSocketClient.btnCexPlusUnSubscribeTradeClick(Sender: TObject);
begin
  CEX_PLUS.UnSubscribeTrade(txtCexPlusPair.Text);
end;


procedure TfrmWebSocketClient.btnCexPlusGetCandlesClick(Sender: TObject);
begin
  CEX_PLUS.GetCandles(txtCexPlusPair.Text, cxpdtBestAsk,
    TsgcWSCexPlusResolution(cboCexPlusResolution.itemIndex),
    IncDay(Now, -1), 0, 1000);
end;


procedure TfrmWebSocketClient.btnCexPlusGetOrdersClick(Sender: TObject);
begin
  CEX_PLUS.GetOrders;
end;


procedure TfrmWebSocketClient.btnCexPlusGetWalletBalanceClick(Sender: TObject);
begin
  CEX_PLUS.GetWalletBalance;
end;


procedure TfrmWebSocketClient.btnCexPlusSubscribeAccountEventsClick(Sender: TObject);
begin
  CEX_PLUS.SubscribeAccountEvents;
end;


procedure TfrmWebSocketClient.btnCexPlusUnSubscribeAccountEventsClick(Sender: TObject);
begin
  CEX_PLUS.UnSubscribeAccountEvents;
end;


procedure TfrmWebSocketClient.CEX_PLUSCexPlusAuthenticated(Sender: TObject);
begin
  DoLog('#authenticated');
end;


procedure TfrmWebSocketClient.CEX_PLUSCexPlusConnect(Sender: TObject);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.CEX_PLUSCexPlusDisconnect(Sender: TObject);
begin
  DoLog('#disconnected from CEX Plus');
end;


procedure TfrmWebSocketClient.CEX_PLUSCexPlusDisconnecting(Sender: TObject;
  Reason, Time: string);
begin
  DoLog('#disconnecting from CEX Plus: ' + Reason);
end;


procedure TfrmWebSocketClient.CEX_PLUSCexPlusError(Sender: TObject;
  Error: string);
begin
  DoLog('#error: ' + Error);
end;


procedure TfrmWebSocketClient.CEX_PLUSCexPlusMessage(Sender: TObject;
  Event, Msg: string);
begin
  DoLog(Msg);
end;


procedure TfrmWebSocketClient.CEX_PLUSCexPlusSubscribed(Sender: TObject;
  Channel: string);
begin
  DoLog('#subscribed: ' + Channel);
end;


procedure TfrmWebSocketClient.CEX_PLUSDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.tabCEX_PLUSShow(Sender: TObject);
begin
  DoServerCEX_PLUS;
end;


procedure TfrmWebSocketClient.DoServerCEX_PLUS;
begin
  DoClear;
  CEX_PLUS.Client := WSClient;

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


procedure TfrmWebSocketClient.txtCexPlusApiKeyChange(Sender: TObject);
begin
  CEX_PLUS.CexPlus.ApiKey := txtCexPlusApiKey.Text;
  DoServerCEX_PLUS;
end;


procedure TfrmWebSocketClient.txtCexPlusApiSecretChange(Sender: TObject);
begin
  CEX_PLUS.CexPlus.ApiSecret := txtCexPlusApiSecret.Text;
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
  CEX_PLUS.Client := nil;
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

