# TsgcWSAPI_Huobi - Example

Full source of `uHuobi.pas` from the **05.Crypto/03.Huobi** demo, which uses `TsgcWSAPI_Huobi`.

API reference: [TsgcWSAPI_Huobi](../reference/api/TsgcWSAPI_Huobi.md)
Source demo: `05.Crypto/03.Huobi` (file `uHuobi.pas`)

```pascal
unit uHuobi;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_Huobi;

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
    tabHUOBI: TTabSheet;
    HUOBI: TsgcWSAPI_Huobi;
    btnSubscribeHuobiKLine: TButton;
    btnUnSubscribeHuobiKLine: TButton;
    cboHuobiPeriods: TComboBox;
    btnSubscribeHuobiMarketDepth: TButton;
    btnUnSubscribeHuobiMarketDepth: TButton;
    cboHuobiDepths: TComboBox;
    btnSubscribeHuobiTradeDetail: TButton;
    btnUnSubscribeHuobiTradeDetail: TButton;
    btnUnSubscribeHuobiMarketDetail: TButton;
    btnSubscribeHuobiMarketDetail: TButton;
    btnSubscribeHuobiMarketTickers: TButton;
    btnUnSubscribeHuobiMarketTickers: TButton;
    pnlHuobiTop: TPanel;
    Label78: TLabel;
    Label79: TLabel;
    Label81: TLabel;
    txtHuobiApiKey: TEdit;
    txtHuobiSymbol: TEdit;
    txtHuobiApiSecret: TEdit;
    pnlHuobiClient: TPanel;
    btnSubscribeHuobiMBP: TButton;
    btnUnSubscribeHuobiMBP: TButton;
    cboHuobiMBPLevels: TComboBox;
    btnSubscribeHuobiAccountChange: TButton;
    cboHuobiAccountMode: TComboBox;
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnSubscribeHuobiKLineClick(Sender: TObject);
    procedure btnSubscribeHuobiMarketDepthClick(Sender: TObject);
    procedure btnSubscribeHuobiMarketDetailClick(Sender: TObject);
    procedure btnSubscribeHuobiMarketTickersClick(Sender: TObject);
    procedure btnSubscribeHuobiTradeDetailClick(Sender: TObject);
    procedure btnUnSubscribeHuobiKLineClick(Sender: TObject);
    procedure btnUnSubscribeHuobiMarketDepthClick(Sender: TObject);
    procedure btnUnSubscribeHuobiMarketDetailClick(Sender: TObject);
    procedure btnUnSubscribeHuobiMarketTickersClick(Sender: TObject);
    procedure btnUnSubscribeHuobiTradeDetailClick(Sender: TObject);
    procedure btnSubscribeHuobiMBPClick(Sender: TObject);
    procedure btnUnSubscribeHuobiMBPClick(Sender: TObject);
    procedure btnSubscribeHuobiAccountChangeClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure HUOBIConnect(Connection: TsgcWSConnection);
    procedure HUOBIDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure HUOBIHuobiError(Sender: TObject; Id, Code, Msg, Ts: string);
    procedure HUOBIHuobiSubscribed(Sender: TObject; Topic, Ts: string);
    procedure HUOBIHuobiUnSubscribed(Sender: TObject; Topic, Ts: string);
    procedure HUOBIHuobiUpdate(Sender: TObject; Data: string);
    procedure tabHUOBIShow(Sender: TObject);
    procedure txtHuobiApiKeyChange(Sender: TObject);
    procedure txtHuobiApiSecretChange(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServerHUOBI;
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


procedure TfrmWebSocketClient.btnSubscribeHuobiKLineClick(Sender: TObject);
begin
  HUOBI.SubscribeKLine(txtHuobiSymbol.Text,
    TsgcWSHuobiPeriods(cboHuobiPeriods.itemIndex));
end;


procedure TfrmWebSocketClient.btnSubscribeHuobiMarketDepthClick
  (Sender: TObject);
begin
  HUOBI.SubscribeMarketDepth(txtHuobiSymbol.Text,
    TsgcWSHuobiDepths(cboHuobiDepths.itemIndex));
end;


procedure TfrmWebSocketClient.btnSubscribeHuobiMarketDetailClick
  (Sender: TObject);
begin
  HUOBI.SubscribeMarketDetail(txtHuobiSymbol.Text);
end;


procedure TfrmWebSocketClient.btnSubscribeHuobiMarketTickersClick
  (Sender: TObject);
begin
  HUOBI.SubscribeMarketTicker(txtHuobiSymbol.Text);
end;


procedure TfrmWebSocketClient.btnSubscribeHuobiTradeDetailClick
  (Sender: TObject);
begin
  HUOBI.SubscribeTradeDetail(txtHuobiSymbol.Text);
end;


procedure TfrmWebSocketClient.btnUnSubscribeHuobiKLineClick(Sender: TObject);
begin
  HUOBI.UnSubscribeKLine(txtHuobiSymbol.Text,
    TsgcWSHuobiPeriods(cboHuobiPeriods.itemIndex));
end;


procedure TfrmWebSocketClient.btnUnSubscribeHuobiMarketDepthClick
  (Sender: TObject);
begin
  HUOBI.UnSubscribeMarketDepth(txtHuobiSymbol.Text,
    TsgcWSHuobiDepths(cboHuobiDepths.itemIndex));
end;


procedure TfrmWebSocketClient.btnUnSubscribeHuobiMarketDetailClick
  (Sender: TObject);
begin
  HUOBI.UnSubscribeMarketDetail(txtHuobiSymbol.Text);
end;


procedure TfrmWebSocketClient.btnUnSubscribeHuobiMarketTickersClick
  (Sender: TObject);
begin
  HUOBI.UnSubscribeMarketTicker(txtHuobiSymbol.Text);
end;


procedure TfrmWebSocketClient.btnUnSubscribeHuobiTradeDetailClick
  (Sender: TObject);
begin
  HUOBI.UnSubscribeTradeDetail(txtHuobiSymbol.Text);
end;


procedure TfrmWebSocketClient.btnSubscribeHuobiMBPClick(Sender: TObject);
begin
  HUOBI.SubscribeMarketByPrice(txtHuobiSymbol.Text,
    TsgcWSHuobiLevels(cboHuobiMBPLevels.ItemIndex));
end;


procedure TfrmWebSocketClient.btnUnSubscribeHuobiMBPClick(Sender: TObject);
begin
  HUOBI.UnSubscribeMarketByPrice(txtHuobiSymbol.Text,
    TsgcWSHuobiLevels(cboHuobiMBPLevels.ItemIndex));
end;


procedure TfrmWebSocketClient.btnSubscribeHuobiAccountChangeClick
  (Sender: TObject);
begin
  HUOBI.SubscribeAccountChange(cboHuobiAccountMode.ItemIndex);
end;


procedure TfrmWebSocketClient.DoServerHUOBI;
begin
  DoClear;
  HUOBI.Client := WSClient;

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


procedure TfrmWebSocketClient.HUOBIConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.HUOBIDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.HUOBIHuobiError(Sender: TObject;
  Id, Code, Msg, Ts: string);
begin
  DoLog('#error: ' + Code + ' ' + Msg);
end;


procedure TfrmWebSocketClient.HUOBIHuobiSubscribed(Sender: TObject;
  Topic, Ts: string);
begin
  DoLog('#subscribed: ' + Topic);
end;


procedure TfrmWebSocketClient.HUOBIHuobiUnSubscribed(Sender: TObject;
  Topic, Ts: string);
begin
  DoLog('#unsubscribed: ' + Topic);
end;


procedure TfrmWebSocketClient.HUOBIHuobiUpdate(Sender: TObject; Data: string);
begin
  DoLog(Data);
end;


procedure TfrmWebSocketClient.tabHUOBIShow(Sender: TObject);
begin
  DoServerHUOBI;
end;


procedure TfrmWebSocketClient.txtHuobiApiKeyChange(Sender: TObject);
begin
  HUOBI.Huobi.ApiKey := txtHuobiApiKey.Text;
  DoServerHUOBI;
end;


procedure TfrmWebSocketClient.txtHuobiApiSecretChange(Sender: TObject);
begin
  HUOBI.Huobi.ApiSecret := txtHuobiApiSecret.Text;
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
  HUOBI.Client := nil;
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

