# TsgcWSAPI_Bitget - Example

Full source of `uBitget.pas` from the **05.Crypto/16.Bitget** demo, which uses `TsgcWSAPI_Bitget`.

API reference: [TsgcWSAPI_Bitget](../reference/api/TsgcWSAPI_Bitget.md)
Source demo: `05.Crypto/16.Bitget` (file `uBitget.pas`)

```pascal
unit uBitget;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_Bitget, sgcHTTP_API_Bitget;

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
    chkTLS: TCheckBox;
    txtHost: TEdit;
    Label5: TLabel;
    txtPort: TEdit;
    pnlTop: TPanel;
    PageControl1: TPageControl;
    pnlMemo: TPanel;
    Label14: TLabel;
    txtParameters: TEdit;
    chkOverWebSocket: TCheckBox;
    Bitget: TsgcWSAPI_Bitget;
    tabBitget: TTabSheet;
    Panel1: TPanel;
    Label1: TLabel;
    Label2: TLabel;
    Label6: TLabel;
    Label7: TLabel;
    txtBitgetAPIKey: TEdit;
    txtBitgetSymbol: TEdit;
    txtBitgetAPISecret: TEdit;
    txtBitgetPassphrase: TEdit;
    PageControl2: TPageControl;
    tabWebSocket: TTabSheet;
    tabREST: TTabSheet;
    GroupBox1: TGroupBox;
    btnSubscribeTicker: TButton;
    btnUnSubscribeTicker: TButton;
    btnSubscribeTrade: TButton;
    btnUnSubscribeTrade: TButton;
    btnSubscribeCandle: TButton;
    btnUnSubscribeCandle: TButton;
    btnSubscribeOrderBook: TButton;
    btnUnSubscribeOrderBook: TButton;
    btnSubscribeOrders: TButton;
    btnUnSubscribeOrders: TButton;
    btnSubscribePositions: TButton;
    btnUnSubscribePositions: TButton;
    btnSubscribeAccount: TButton;
    btnUnSubscribeAccount: TButton;
    GroupBox2: TGroupBox;
    btnBitgetServerTime: TButton;
    btnBitgetTickers: TButton;
    btnBitgetOrderBook: TButton;
    btnBitgetAccountAssets: TButton;
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnSubscribeTickerClick(Sender: TObject);
    procedure btnUnSubscribeTickerClick(Sender: TObject);
    procedure btnSubscribeTradeClick(Sender: TObject);
    procedure btnUnSubscribeTradeClick(Sender: TObject);
    procedure btnSubscribeCandleClick(Sender: TObject);
    procedure btnUnSubscribeCandleClick(Sender: TObject);
    procedure btnSubscribeOrderBookClick(Sender: TObject);
    procedure btnUnSubscribeOrderBookClick(Sender: TObject);
    procedure btnSubscribeOrdersClick(Sender: TObject);
    procedure btnUnSubscribeOrdersClick(Sender: TObject);
    procedure btnSubscribePositionsClick(Sender: TObject);
    procedure btnUnSubscribePositionsClick(Sender: TObject);
    procedure btnSubscribeAccountClick(Sender: TObject);
    procedure btnUnSubscribeAccountClick(Sender: TObject);
    procedure btnBitgetServerTimeClick(Sender: TObject);
    procedure btnBitgetTickersClick(Sender: TObject);
    procedure btnBitgetOrderBookClick(Sender: TObject);
    procedure btnBitgetAccountAssetsClick(Sender: TObject);
    procedure BitgetBitgetAuthentication(Sender: TObject; aSuccess: Boolean;
      const aError, aRawMessage: string);
    procedure BitgetBitgetData(Sender: TObject; const aData: string);
    procedure BitgetBitgetError(Sender: TObject; aErrorCode: string;
      const aErrorMessage, aRawMessage: string);
    procedure BitgetBitgetSubscribe(Sender: TObject;
      aSuccess: Boolean; const aError, aRawMessage: string);
    procedure BitgetBitgetUnSubscribe(Sender: TObject;
      aSuccess: Boolean; const aError, aRawMessage: string);
    procedure BitgetConnect(Connection: TsgcWSConnection);
    procedure BitgetDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure txtBitgetAPIKeyChange(Sender: TObject);
    procedure txtBitgetAPISecretChange(Sender: TObject);
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
  sgcWebSocket_Helpers, sgcJSON, StrUtils, sgcBase_Helpers;
{$R *.dfm}

procedure TfrmWebSocketClient.FormCreate(Sender: TObject);
begin
  Bitget.Client := WSClient;

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

procedure TfrmWebSocketClient.btnSubscribeTickerClick(Sender: TObject);
begin
  Bitget.SubscribeTicker(txtBitgetSymbol.Text);
end;

procedure TfrmWebSocketClient.btnUnSubscribeTickerClick(Sender: TObject);
begin
  Bitget.UnSubscribeTicker(txtBitgetSymbol.Text);
end;

procedure TfrmWebSocketClient.btnSubscribeTradeClick(Sender: TObject);
begin
  Bitget.SubscribeTrade(txtBitgetSymbol.Text);
end;

procedure TfrmWebSocketClient.btnUnSubscribeTradeClick(Sender: TObject);
begin
  Bitget.UnSubscribeTrade(txtBitgetSymbol.Text);
end;

procedure TfrmWebSocketClient.btnSubscribeCandleClick(Sender: TObject);
begin
  Bitget.SubscribeCandle(txtBitgetSymbol.Text);
end;

procedure TfrmWebSocketClient.btnUnSubscribeCandleClick(Sender: TObject);
begin
  Bitget.UnSubscribeCandle(txtBitgetSymbol.Text);
end;

procedure TfrmWebSocketClient.btnSubscribeOrderBookClick(Sender: TObject);
begin
  Bitget.SubscribeOrderBook(txtBitgetSymbol.Text);
end;

procedure TfrmWebSocketClient.btnUnSubscribeOrderBookClick(Sender: TObject);
begin
  Bitget.UnSubscribeOrderBook(txtBitgetSymbol.Text);
end;

procedure TfrmWebSocketClient.btnSubscribeOrdersClick(Sender: TObject);
begin
  Bitget.SubscribeOrders(txtBitgetSymbol.Text);
end;

procedure TfrmWebSocketClient.btnUnSubscribeOrdersClick(Sender: TObject);
begin
  Bitget.UnSubscribeOrders(txtBitgetSymbol.Text);
end;

procedure TfrmWebSocketClient.btnSubscribePositionsClick(Sender: TObject);
begin
  Bitget.SubscribePositions(txtBitgetSymbol.Text, 'USDT-FUTURES');
end;

procedure TfrmWebSocketClient.btnUnSubscribePositionsClick(Sender: TObject);
begin
  Bitget.UnSubscribePositions(txtBitgetSymbol.Text, 'USDT-FUTURES');
end;

procedure TfrmWebSocketClient.btnSubscribeAccountClick(Sender: TObject);
begin
  Bitget.SubscribeAccount;
end;

procedure TfrmWebSocketClient.btnUnSubscribeAccountClick(Sender: TObject);
begin
  Bitget.UnSubscribeAccount;
end;

procedure TfrmWebSocketClient.btnBitgetServerTimeClick(Sender: TObject);
begin
  DoLog(Bitget.REST_API.GetServerTime);
end;

procedure TfrmWebSocketClient.btnBitgetTickersClick(Sender: TObject);
begin
  DoLog(Bitget.REST_API.GetTickers('SPOT', txtBitgetSymbol.Text));
end;

procedure TfrmWebSocketClient.btnBitgetOrderBookClick(Sender: TObject);
begin
  DoLog(Bitget.REST_API.GetOrderBook(txtBitgetSymbol.Text));
end;

procedure TfrmWebSocketClient.btnBitgetAccountAssetsClick(Sender: TObject);
begin
  DoLog(Bitget.REST_API.GetAccountAssets);
end;

procedure TfrmWebSocketClient.BitgetBitgetAuthentication(Sender: TObject;
  aSuccess: Boolean; const aError, aRawMessage: string);
begin
  if aSuccess then
    DoLog('#Bitget Authenticated')
  else
    DoLog('#Bitget Authentication error: ' + aError);
end;

procedure TfrmWebSocketClient.BitgetBitgetData(Sender: TObject;
  const aData: string);
begin
  DoLog(aData);
end;

procedure TfrmWebSocketClient.BitgetBitgetError(Sender: TObject;
  aErrorCode: string; const aErrorMessage, aRawMessage: string);
begin
  DoLog('#Bitget Error: ' + aErrorMessage);
end;

procedure TfrmWebSocketClient.BitgetBitgetSubscribe(Sender: TObject;
  aSuccess: Boolean; const aError, aRawMessage: string);
begin
  if aSuccess then
    DoLog('#Bitget subscribe ok')
  else
    DoLog('#Bitget subscribe error: ' + aError);
end;

procedure TfrmWebSocketClient.BitgetBitgetUnSubscribe(Sender: TObject;
  aSuccess: Boolean; const aError, aRawMessage: string);
begin
  if aSuccess then
    DoLog('#Bitget unsubscribe ok')
  else
    DoLog('#Bitget unsubscribe error: ' + aError);
end;

procedure TfrmWebSocketClient.BitgetConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;

procedure TfrmWebSocketClient.BitgetDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;

procedure TfrmWebSocketClient.FormClose(Sender: TObject;
  var Action: TCloseAction);
begin
  WSClient.Active := False;
end;

procedure TfrmWebSocketClient.txtBitgetAPIKeyChange(Sender: TObject);
begin
  Bitget.Bitget.ApiKey := txtBitgetAPIKey.Text;
end;

procedure TfrmWebSocketClient.txtBitgetAPISecretChange(Sender: TObject);
begin
  Bitget.Bitget.ApiSecret := txtBitgetAPISecret.Text;
end;

procedure TfrmWebSocketClient.DoClear;
begin
  Bitget.Client := nil;
end;

procedure TfrmWebSocketClient.DoBeforeConnect;
begin
end;

procedure TfrmWebSocketClient.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
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

end.
```

