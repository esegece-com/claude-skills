# TsgcWSAPI_HTX - Example

Full source of `uHTX.pas` from the **05.Crypto/20.HTX** demo, which uses `TsgcWSAPI_HTX`.

API reference: [TsgcWSAPI_HTX](../reference/api/TsgcWSAPI_HTX.md)
Source demo: `05.Crypto/20.HTX` (file `uHTX.pas`)

```pascal
unit uHTX;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, ExtCtrls, ComCtrls, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_Client, sgcWebSocket, sgcWebSocket_Protocol_Base_Client,
  sgcWebSocket_Protocols, sgcWebSocket_Types, sgcWebSocket_Classes_Indy,
  sgcWebSocket_APIs, sgcBase_Classes, sgcTCP_Classes, sgcHTTP,
  sgcSocket_Classes, sgcWebSocket_API_Huobi, sgcHTTP_API_HTX;

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
    Label14: TLabel;
    txtParameters: TEdit;
    pnlTop: TPanel;
    PageControl1: TPageControl;
    pnlMemo: TPanel;
    HTX: TsgcWSAPI_HTX;
    tabHTX: TTabSheet;
    Panel9: TPanel;
    Label45: TLabel;
    Label46: TLabel;
    Label84: TLabel;
    txtHTXAPIKey: TEdit;
    txtHTXSymbol: TEdit;
    txtHTXAPISecret: TEdit;
    PageControl8: TPageControl;
    tabHTXWebSocket: TTabSheet;
    GroupBox15: TGroupBox;
    btnHTXSubscribeKLine: TButton;
    btnHTXUnSubscribeKLine: TButton;
    btnHTXSubscribeMarketDepth: TButton;
    btnHTXUnSubscribeMarketDepth: TButton;
    btnHTXSubscribeTradeDetail: TButton;
    btnHTXUnSubscribeTradeDetail: TButton;
    btnHTXSubscribeMarketDetail: TButton;
    btnHTXUnSubscribeMarketDetail: TButton;
    btnHTXSubscribeMarketTicker: TButton;
    btnHTXUnSubscribeMarketTicker: TButton;
    tabHTXRESTApi: TTabSheet;
    GroupBox19: TGroupBox;
    btnHTXRESTGetServerTime: TButton;
    btnHTXRESTGetMarketTickers: TButton;
    btnHTXRESTGetMarketDepth: TButton;
    btnHTXRESTGetMarketDetail: TButton;
    btnHTXRESTGetAccounts: TButton;
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure WSClientConnect(Connection: TsgcWSConnection);
    procedure WSClientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSClientError(Connection: TsgcWSConnection; const Error: string);
    procedure WSClientException(Connection: TsgcWSConnection; E: Exception);
    procedure WSClientMessage(Connection: TsgcWSConnection; const Text: string);
    procedure HTXConnect(Connection: TsgcWSConnection);
    procedure HTXDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure HTXHuobiSubscribed(Sender: TObject; Topic, Ts: String);
    procedure HTXHuobiUnSubscribed(Sender: TObject; Topic, Ts: String);
    procedure HTXHuobiUpdate(Sender: TObject; Data: String);
    procedure HTXHuobiError(Sender: TObject; Id, Code, Msg, Ts: string);
    procedure btnHTXSubscribeKLineClick(Sender: TObject);
    procedure btnHTXUnSubscribeKLineClick(Sender: TObject);
    procedure btnHTXSubscribeMarketDepthClick(Sender: TObject);
    procedure btnHTXUnSubscribeMarketDepthClick(Sender: TObject);
    procedure btnHTXSubscribeTradeDetailClick(Sender: TObject);
    procedure btnHTXUnSubscribeTradeDetailClick(Sender: TObject);
    procedure btnHTXSubscribeMarketDetailClick(Sender: TObject);
    procedure btnHTXUnSubscribeMarketDetailClick(Sender: TObject);
    procedure btnHTXSubscribeMarketTickerClick(Sender: TObject);
    procedure btnHTXUnSubscribeMarketTickerClick(Sender: TObject);
    procedure btnHTXRESTGetServerTimeClick(Sender: TObject);
    procedure btnHTXRESTGetMarketTickersClick(Sender: TObject);
    procedure btnHTXRESTGetMarketDepthClick(Sender: TObject);
    procedure btnHTXRESTGetMarketDetailClick(Sender: TObject);
    procedure btnHTXRESTGetAccountsClick(Sender: TObject);
    procedure FormClose(Sender: TObject; var Action: TCloseAction);
    procedure FormDestroy(Sender: TObject);
  private
    procedure DoLog(const aText: String);
  private
    FREST_API: TsgcHTTP_API_HTX;
    function GetREST_API: TsgcHTTP_API_HTX;
  public
    property REST_API: TsgcHTTP_API_HTX read GetREST_API;
  end;

var
  frmWebSocketClient: TfrmWebSocketClient;

implementation

uses
  sgcBase_Helpers;
{$R *.dfm}

procedure TfrmWebSocketClient.FormCreate(Sender: TObject);
begin
  HTX.Client := WSClient;

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

  HTX.Huobi.ApiKey := txtHTXAPIKey.Text;
  HTX.Huobi.ApiSecret := txtHTXAPISecret.Text;

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


procedure TfrmWebSocketClient.FormClose(Sender: TObject;
  var Action: TCloseAction);
begin
  WSClient.Active := False;
end;


procedure TfrmWebSocketClient.FormDestroy(Sender: TObject);
begin
  sgcFree(FREST_API);
end;


function TfrmWebSocketClient.GetREST_API: TsgcHTTP_API_HTX;
begin
  if not Assigned(FREST_API) then
  begin
    FREST_API := TsgcHTTP_API_HTX.Create(nil);
    FREST_API.HTXOptions.ApiKey := txtHTXAPIKey.Text;
    FREST_API.HTXOptions.ApiSecret := txtHTXAPISecret.Text;
  end;
  Result := FREST_API;
end;


procedure TfrmWebSocketClient.HTXConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;


procedure TfrmWebSocketClient.HTXDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;


procedure TfrmWebSocketClient.HTXHuobiSubscribed(Sender: TObject;
  Topic, Ts: String);
begin
  DoLog('#HTX subscribed: ' + Topic);
end;


procedure TfrmWebSocketClient.HTXHuobiUnSubscribed(Sender: TObject;
  Topic, Ts: String);
begin
  DoLog('#HTX unsubscribed: ' + Topic);
end;


procedure TfrmWebSocketClient.HTXHuobiUpdate(Sender: TObject; Data: String);
begin
  DoLog(Data);
end;


procedure TfrmWebSocketClient.HTXHuobiError(Sender: TObject;
  Id, Code, Msg, Ts: string);
begin
  DoLog('#HTX Error: ' + Code + ' - ' + Msg);
end;


procedure TfrmWebSocketClient.btnHTXSubscribeKLineClick(Sender: TObject);
begin
  HTX.SubscribeKLine(txtHTXSymbol.Text, hup1Min);
end;


procedure TfrmWebSocketClient.btnHTXUnSubscribeKLineClick(Sender: TObject);
begin
  HTX.UnSubscribeKLine(txtHTXSymbol.Text, hup1Min);
end;


procedure TfrmWebSocketClient.btnHTXSubscribeMarketDepthClick(Sender: TObject);
begin
  HTX.SubscribeMarketDepth(txtHTXSymbol.Text, hudStep0);
end;


procedure TfrmWebSocketClient.btnHTXUnSubscribeMarketDepthClick(Sender: TObject);
begin
  HTX.UnSubscribeMarketDepth(txtHTXSymbol.Text, hudStep0);
end;


procedure TfrmWebSocketClient.btnHTXSubscribeTradeDetailClick(Sender: TObject);
begin
  HTX.SubscribeTradeDetail(txtHTXSymbol.Text);
end;


procedure TfrmWebSocketClient.btnHTXUnSubscribeTradeDetailClick(Sender: TObject);
begin
  HTX.UnSubscribeTradeDetail(txtHTXSymbol.Text);
end;


procedure TfrmWebSocketClient.btnHTXSubscribeMarketDetailClick(Sender: TObject);
begin
  HTX.SubscribeMarketDetail(txtHTXSymbol.Text);
end;


procedure TfrmWebSocketClient.btnHTXUnSubscribeMarketDetailClick(Sender: TObject);
begin
  HTX.UnSubscribeMarketDetail(txtHTXSymbol.Text);
end;


procedure TfrmWebSocketClient.btnHTXSubscribeMarketTickerClick(Sender: TObject);
begin
  HTX.SubscribeMarketTicker(txtHTXSymbol.Text);
end;


procedure TfrmWebSocketClient.btnHTXUnSubscribeMarketTickerClick(Sender: TObject);
begin
  HTX.UnSubscribeMarketTicker(txtHTXSymbol.Text);
end;


procedure TfrmWebSocketClient.btnHTXRESTGetServerTimeClick(Sender: TObject);
begin
  DoLog(REST_API.GetServerTime);
end;


procedure TfrmWebSocketClient.btnHTXRESTGetMarketTickersClick(Sender: TObject);
begin
  DoLog(REST_API.GetMarketTickers);
end;


procedure TfrmWebSocketClient.btnHTXRESTGetMarketDepthClick(Sender: TObject);
begin
  DoLog(REST_API.GetMarketDepth(txtHTXSymbol.Text));
end;


procedure TfrmWebSocketClient.btnHTXRESTGetMarketDetailClick(Sender: TObject);
begin
  DoLog(REST_API.GetMarketDetail(txtHTXSymbol.Text));
end;


procedure TfrmWebSocketClient.btnHTXRESTGetAccountsClick(Sender: TObject);
begin
  DoLog(REST_API.GetAccounts);
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


procedure TfrmWebSocketClient.DoLog(const aText: String);
begin
  memoLog.Lines.Add(aText);
end;

end.
```

