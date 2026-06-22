# TsgcWSAPI_ThreeCommas - Example

Full source of `uThreeCommas.pas` from the **05.Crypto/10.ThreeCommas** demo, which uses `TsgcWSAPI_ThreeCommas`.

API reference: [TsgcWSAPI_ThreeCommas](../reference/api/TsgcWSAPI_ThreeCommas.md)
Source demo: `05.Crypto/10.ThreeCommas` (file `uThreeCommas.pas`)

```pascal
unit uThreeCommas;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_ThreeCommas, sgcHTTP_API_ThreeCommas;

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
    tabThreeCommas: TTabSheet;
    THREE_COMMAS: TsgcWSAPI_ThreeCommas;
    Label75: TLabel;
    Label82: TLabel;
    txtThreeCommasApiSecret: TEdit;
    txtThreeCommasApiKey: TEdit;
    PageControl5: TPageControl;
    TabSheet6: TTabSheet;
    btnThreeComasSubscribeSmartTrades: TButton;
    btnThreeComasSubscribeDeals: TButton;
    TabSheet8: TTabSheet;
    Label85: TLabel;
    Label86: TLabel;
    Label87: TLabel;
    Label88: TLabel;
    Label89: TLabel;
    Label90: TLabel;
    btnThreeCommasGetAccounts: TButton;
    btnThreeCommasGetMarketList: TButton;
    btnThreeCommasMarketOrder: TButton;
    cboThreeCommasMarketSide: TComboBox;
    cboThreeCommasLimitSide: TComboBox;
    btnThreeCommasLimitOrder: TButton;
    txtThreeCommasMarketSize: TEdit;
    txtThreeCommasLimitSize: TEdit;
    txtThreeCommasLimitPrice: TEdit;
    btnThreeCommasGetBalances: TButton;
    txtThreeCommasAccountId: TEdit;
    btnThreeCommasGetAccountTableData: TButton;
    btnThreeCommasGetAccountInfo: TButton;
    Label83: TLabel;
    txtThreeCommasPair: TEdit;
    btnThreeCommasGetDCABots: TButton;
    btnThreeCommasGetDeals: TButton;
    btnThreeCommasGetGridBots: TButton;
    btnThreeCommasGetDCABotStats: TButton;
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnThreeComasSubscribeDealsClick(Sender: TObject);
    procedure btnThreeComasSubscribeSmartTradesClick(Sender: TObject);
    procedure btnThreeCommasGetAccountInfoClick(Sender: TObject);
    procedure btnThreeCommasGetAccountsClick(Sender: TObject);
    procedure btnThreeCommasGetAccountTableDataClick(Sender: TObject);
    procedure btnThreeCommasGetBalancesClick(Sender: TObject);
    procedure btnThreeCommasGetMarketListClick(Sender: TObject);
    procedure btnThreeCommasMarketOrderClick(Sender: TObject);
    procedure btnThreeCommasLimitOrderClick(Sender: TObject);
    procedure btnThreeCommasGetDCABotsClick(Sender: TObject);
    procedure btnThreeCommasGetDealsClick(Sender: TObject);
    procedure btnThreeCommasGetGridBotsClick(Sender: TObject);
    procedure btnThreeCommasGetDCABotStatsClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure tabThreeCommasShow(Sender: TObject);
    procedure THREE_COMMASConnect(Connection: TsgcWSConnection);
    procedure THREE_COMMASDisconnect(Connection: TsgcWSConnection;
      Code: Integer);
    procedure THREE_COMMASThreeCommasConfirmSubscription(Sender: TObject;
      const aChannel, aRawMessage: string);
    procedure THREE_COMMASThreeCommasConnect(Sender: TObject;
      const aRawMessage: string);
    procedure THREE_COMMASThreeCommasHTTPException(Sender: TObject;
      E: Exception);
    procedure THREE_COMMASThreeCommasMessage(Sender: TObject;
      const aType, aRawMessage: string);
    procedure THREE_COMMASThreeCommasPing(Sender: TObject;
      const aRawMessage: string);
    procedure THREE_COMMASThreeCommasRejectSubscription(Sender: TObject;
      const aChannel, aRawMessage: string);
    procedure txtThreeCommasApiKeyChange(Sender: TObject);
    procedure txtThreeCommasApiSecretChange(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServer3Commas;
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


procedure TfrmWebSocketClient.btnThreeComasSubscribeDealsClick(Sender: TObject);
begin
  THREE_COMMAS.SubscribeDeals;
end;


procedure TfrmWebSocketClient.btnThreeComasSubscribeSmartTradesClick
  (Sender: TObject);
begin
  THREE_COMMAS.SubscribeSmartTrades;
end;


procedure TfrmWebSocketClient.btnThreeCommasGetAccountInfoClick
  (Sender: TObject);
begin
  DoLog(THREE_COMMAS.REST_API.GetAccountInfo
    (StrToInt(txtThreeCommasAccountId.Text)));
end;


procedure TfrmWebSocketClient.btnThreeCommasGetAccountsClick(Sender: TObject);
begin
  DoLog(THREE_COMMAS.REST_API.GetAccounts);
end;


procedure TfrmWebSocketClient.btnThreeCommasGetAccountTableDataClick
  (Sender: TObject);
begin
  DoLog(THREE_COMMAS.REST_API.GetAccountTableData
    (StrToInt(txtThreeCommasAccountId.Text)));
end;


procedure TfrmWebSocketClient.btnThreeCommasGetBalancesClick(Sender: TObject);
begin
  DoLog(THREE_COMMAS.REST_API.GetBalances
    (StrToInt(txtThreeCommasAccountId.Text)));
end;


procedure TfrmWebSocketClient.btnThreeCommasGetMarketListClick(Sender: TObject);
begin
  DoLog(THREE_COMMAS.REST_API.GetMarketList);
end;


procedure TfrmWebSocketClient.btnThreeCommasMarketOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPThreeCommasOrderSide;
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  if cboThreeCommasMarketSide.itemIndex = 0 then
    vSide := os3cBuy
  else
    vSide := os3cSell;

  DoLog(THREE_COMMAS.REST_API.PlaceMarketOrder
    (StrToInt(txtThreeCommasAccountId.Text), vSide, txtThreeCommasPair.Text,
    StrToFloat(txtThreeCommasMarketSize.Text, vFS)));
end;


procedure TfrmWebSocketClient.btnThreeCommasLimitOrderClick(Sender: TObject);
var
  vSide: TsgcHTTPThreeCommasOrderSide;
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  if cboThreeCommasLimitSide.itemIndex = 0 then
    vSide := os3cBuy
  else
    vSide := os3cSell;

  DoLog(THREE_COMMAS.REST_API.PlaceLimitOrder
    (StrToInt(txtThreeCommasAccountId.Text), vSide, txtThreeCommasPair.Text,
    StrToFloat(txtThreeCommasLimitSize.Text, vFS),
    StrToFloat(txtThreeCommasLimitPrice.Text, vFS)));
end;


procedure TfrmWebSocketClient.btnThreeCommasGetDCABotsClick(Sender: TObject);
begin
  DoLog(THREE_COMMAS.REST_API.GetDCABots);
end;


procedure TfrmWebSocketClient.btnThreeCommasGetDealsClick(Sender: TObject);
begin
  DoLog(THREE_COMMAS.REST_API.GetDeals);
end;


procedure TfrmWebSocketClient.btnThreeCommasGetGridBotsClick(Sender: TObject);
begin
  DoLog(THREE_COMMAS.REST_API.GetGridBots);
end;


procedure TfrmWebSocketClient.btnThreeCommasGetDCABotStatsClick(Sender: TObject);
begin
  DoLog(THREE_COMMAS.REST_API.GetDCABotStats);
end;


procedure TfrmWebSocketClient.DoServer3Commas;
begin
  DoClear;
  THREE_COMMAS.Client := WSClient;

  txtParameters.Text := '/';
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


procedure TfrmWebSocketClient.tabThreeCommasShow(Sender: TObject);
begin
  DoServer3Commas;
end;


procedure TfrmWebSocketClient.THREE_COMMASConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.THREE_COMMASDisconnect
  (Connection: TsgcWSConnection; Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.THREE_COMMASThreeCommasConfirmSubscription
  (Sender: TObject; const aChannel, aRawMessage: string);
begin
  DoLog(aRawMessage);
end;


procedure TfrmWebSocketClient.THREE_COMMASThreeCommasConnect(Sender: TObject;
  const aRawMessage: string);
begin
  DoLog('#3Commas connected');
end;


procedure TfrmWebSocketClient.THREE_COMMASThreeCommasHTTPException
  (Sender: TObject; E: Exception);
begin
  DoLog(E.Message);
end;


procedure TfrmWebSocketClient.THREE_COMMASThreeCommasMessage(Sender: TObject;
  const aType, aRawMessage: string);
begin
  DoLog(aRawMessage);
end;


procedure TfrmWebSocketClient.THREE_COMMASThreeCommasPing(Sender: TObject;
  const aRawMessage: string);
begin
  DoLog(aRawMessage);
end;


procedure TfrmWebSocketClient.THREE_COMMASThreeCommasRejectSubscription
  (Sender: TObject; const aChannel, aRawMessage: string);
begin
  DoLog(aRawMessage);
end;


procedure TfrmWebSocketClient.txtThreeCommasApiKeyChange(Sender: TObject);
begin
  THREE_COMMAS.ThreeCommas.ApiKey := txtThreeCommasApiKey.Text;
end;


procedure TfrmWebSocketClient.txtThreeCommasApiSecretChange(Sender: TObject);
begin
  THREE_COMMAS.ThreeCommas.ApiSecret := txtThreeCommasApiSecret.Text;
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
  THREE_COMMAS.Client := nil;
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

