# TsgcWSAPI_Bitfinex - Example

Full source of `uBitfinex.pas` from the **05.Crypto/21.Bitfinex** demo, which uses `TsgcWSAPI_Bitfinex`.

API reference: [TsgcWSAPI_Bitfinex](../reference/api/TsgcWSAPI_Bitfinex.md)
Source demo: `05.Crypto/21.Bitfinex` (file `uBitfinex.pas`)

```pascal
{ ***************************************************************************
  sgcWebSocket component

  written by eSeGeCe
  copyright © 2026
  Email : info@esegece.com
  Web : https://www.esegece.com
  *************************************************************************** }

unit uBitfinex;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_Bitfinex, sgcWebSocket_Client_Base;

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
    BITFINEX: TsgcWSAPI_Bitfinex;
    tabBITFINEX: TTabSheet;
    pageBitfinex: TPageControl;
    tabBitfinexWebSocket: TTabSheet;
    tabBitfinexConfig: TTabSheet;
    pnlBitfinexTop: TPanel;
    Label1: TLabel;
    Label2: TLabel;
    txtSymbol: TEdit;
    txtCandleKey: TEdit;
    btnSubscribeTicker: TButton;
    btnSubscribeTrades: TButton;
    btnSubscribeOrderBook: TButton;
    btnSubscribeRawOrderBook: TButton;
    btnSubscribeCandles: TButton;
    Label15: TLabel;
    Label16: TLabel;
    Label17: TLabel;
    txtUnsubChanId: TEdit;
    btnUnsubscribe: TButton;
    btnPing: TButton;
    btnConfigDecStrings: TButton;
    btnConfigTimeStrings: TButton;
    btnConfigSequencing: TButton;
    btnConfigChecksum: TButton;
    procedure BITFINEXConnect(Connection: TsgcWSConnection);
    procedure BITFINEXDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure BITFINEXMessage(Connection: TsgcWSConnection; const Text: string);
    procedure BITFINEXBitfinexConnect(Sender: TObject; Version: String);
    procedure BITFINEXBitfinexAuth(Sender: TObject; Status: String;
      ChanId, Code: Integer; Msg: String);
    procedure BITFINEXBitfinexUnauth(Sender: TObject; Status: String;
      ChanId: Integer);
    procedure BITFINEXBitfinexInfoMsg(Sender: TObject; Code, Msg: String);
    procedure BITFINEXBitfinexSubscribed(Sender: TObject; Channel: String;
      ChanId: Integer; Symbol, Pair, Key: String);
    procedure BITFINEXBitfinexUnSubscribed(Sender: TObject; Status: String;
      ChanId: Integer);
    procedure BITFINEXBitfinexUpdate(Sender: TObject; Data: String);
    procedure BITFINEXBitfinexError(Sender: TObject; Status: String;
      ChanId, Code: Integer);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure btnSubscribeTickerClick(Sender: TObject);
    procedure btnSubscribeTradesClick(Sender: TObject);
    procedure btnSubscribeOrderBookClick(Sender: TObject);
    procedure btnSubscribeRawOrderBookClick(Sender: TObject);
    procedure btnSubscribeCandlesClick(Sender: TObject);
    procedure btnUnsubscribeClick(Sender: TObject);
    procedure btnPingClick(Sender: TObject);
    procedure btnConfigDecStringsClick(Sender: TObject);
    procedure btnConfigTimeStringsClick(Sender: TObject);
    procedure btnConfigSequencingClick(Sender: TObject);
    procedure btnConfigChecksumClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure tabBITFINEXShow(Sender: TObject);
  private
    procedure DoLog(const aText: String);
    procedure DoClear;
  private
    procedure DoBeforeConnect;
  private
    procedure DoServerBITFINEX;
  end;

var
  frmWebSocketClient: TfrmWebSocketClient;

implementation

uses
  sgcWebSocket_Helpers, sgcJSON, StrUtils, sgcBase_Helpers,
  sgcIdGlobal;
{$R *.dfm}

procedure TfrmWebSocketClient.BITFINEXConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;

procedure TfrmWebSocketClient.BITFINEXDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;

procedure TfrmWebSocketClient.BITFINEXMessage(Connection: TsgcWSConnection;
  const Text: string);
begin
  DoLog(Text);
end;

procedure TfrmWebSocketClient.BITFINEXBitfinexConnect(Sender: TObject;
  Version: String);
begin
  DoLog('#bitfinex connected, version: ' + Version);
end;

procedure TfrmWebSocketClient.BITFINEXBitfinexAuth(Sender: TObject;
  Status: String; ChanId, Code: Integer; Msg: String);
begin
  DoLog('#auth status: ' + Status + ' chanId: ' + IntToStr(ChanId) + ' code: ' +
    IntToStr(Code) + ' msg: ' + Msg);
end;

procedure TfrmWebSocketClient.BITFINEXBitfinexUnauth(Sender: TObject;
  Status: String; ChanId: Integer);
begin
  DoLog('#unauth status: ' + Status + ' chanId: ' + IntToStr(ChanId));
end;

procedure TfrmWebSocketClient.BITFINEXBitfinexInfoMsg(Sender: TObject;
  Code, Msg: String);
begin
  DoLog('#info code: ' + Code + ' msg: ' + Msg);
end;

procedure TfrmWebSocketClient.BITFINEXBitfinexSubscribed(Sender: TObject;
  Channel: String; ChanId: Integer; Symbol, Pair, Key: String);
begin
  DoLog('#subscribed channel: ' + Channel + ' chanId: ' + IntToStr(ChanId) +
    ' symbol: ' + Symbol + ' pair: ' + Pair + ' key: ' + Key);
end;

procedure TfrmWebSocketClient.BITFINEXBitfinexUnSubscribed(Sender: TObject;
  Status: String; ChanId: Integer);
begin
  DoLog('#unsubscribed status: ' + Status + ' chanId: ' + IntToStr(ChanId));
end;

procedure TfrmWebSocketClient.BITFINEXBitfinexUpdate(Sender: TObject;
  Data: String);
begin
  DoLog(Data);
end;

procedure TfrmWebSocketClient.BITFINEXBitfinexError(Sender: TObject;
  Status: String; ChanId, Code: Integer);
begin
  DoLog('#error status: ' + Status + ' chanId: ' + IntToStr(ChanId) + ' code: '
    + IntToStr(Code));
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

procedure TfrmWebSocketClient.btnSubscribeTickerClick(Sender: TObject);
begin
  BITFINEX.SubscribeTicker(txtSymbol.Text);
end;

procedure TfrmWebSocketClient.btnSubscribeTradesClick(Sender: TObject);
begin
  BITFINEX.SubscribeTrades(txtSymbol.Text);
end;

procedure TfrmWebSocketClient.btnSubscribeOrderBookClick(Sender: TObject);
begin
  BITFINEX.SubscribeOrderBook(txtSymbol.Text);
end;

procedure TfrmWebSocketClient.btnSubscribeRawOrderBookClick(Sender: TObject);
begin
  BITFINEX.SubscribeRawOrderBook(txtSymbol.Text);
end;

procedure TfrmWebSocketClient.btnSubscribeCandlesClick(Sender: TObject);
begin
  BITFINEX.SubscribeCandles(txtCandleKey.Text);
end;

procedure TfrmWebSocketClient.btnUnsubscribeClick(Sender: TObject);
var
  vChanId: Integer;
begin
  vChanId := StrToIntDef(txtUnsubChanId.Text, 0);
  BITFINEX.UnSubscribeTicker(vChanId);
end;

procedure TfrmWebSocketClient.btnPingClick(Sender: TObject);
begin
  BITFINEX.Ping;
end;

procedure TfrmWebSocketClient.btnConfigDecStringsClick(Sender: TObject);
begin
  BITFINEX.Configuration(8);
end;

procedure TfrmWebSocketClient.btnConfigTimeStringsClick(Sender: TObject);
begin
  BITFINEX.Configuration(32);
end;

procedure TfrmWebSocketClient.btnConfigSequencingClick(Sender: TObject);
begin
  BITFINEX.Configuration(65536);
end;

procedure TfrmWebSocketClient.btnConfigChecksumClick(Sender: TObject);
begin
  BITFINEX.Configuration(131072);
end;

procedure TfrmWebSocketClient.DoServerBITFINEX;
begin
  DoClear;
  BITFINEX.Client := WSClient;

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

procedure TfrmWebSocketClient.tabBITFINEXShow(Sender: TObject);
begin
  DoServerBITFINEX;
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
  BITFINEX.Client := nil;
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

