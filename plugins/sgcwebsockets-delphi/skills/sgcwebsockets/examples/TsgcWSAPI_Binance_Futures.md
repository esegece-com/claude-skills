# TsgcWSAPI_Binance_Futures - Example

Full source of `FsgcBinanceTradeFutures.pas` from the **02.WebSocket_Protocols/09.Binance_Trade_Futures** demo, which uses `TsgcWSAPI_Binance_Futures`.

API reference: [TsgcWSAPI_Binance_Futures](../reference/api/TsgcWSAPI_Binance_Futures.md)
Source demo: `02.WebSocket_Protocols/09.Binance_Trade_Futures` (file `FsgcBinanceTradeFutures.pas`)

```pascal
unit FsgcBinanceTradeFutures;

interface

uses
  Windows, Messages, SysUtils, Variants,
  Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls, sgcWebSocket_Classes,
  sgcWebSocket_API_Binance, sgcWebSocket_APIs, sgcBase_Classes,
  sgcSocket_Classes, sgcTCP_Classes, sgcWebSocket_Classes_Indy,
  sgcWebSocket_Client, sgcWebSocket;

type
  TFRMSGCBinanceTradeFutures = class(TForm)
    btnNewOrder: TButton;
    Memo1: TMemo;
    txtSymbol: TEdit;
    wsclient: TsgcWebSocketClient;
    binancefut: TsgcWSAPI_Binance_Futures;
    txtApiKey: TEdit;
    txtApiSecret: TEdit;
    Label1: TLabel;
    Label2: TLabel;
    Label3: TLabel;
    cboSide: TComboBox;
    cboOrderType: TComboBox;
    txtQuantity: TEdit;
    Label4: TLabel;
    Label5: TLabel;
    Label6: TLabel;
    txtPrice: TEdit;
    Label7: TLabel;
    btnAllOrders: TButton;
    btnCancelAllOpenOrders: TButton;
    btnSubscribeTicker: TButton;
    btnTickerSnapshot: TButton;
    procedure FormCreate(Sender: TObject);
    procedure binancefutBinanceHTTPException(Sender: TObject; E: Exception);
    procedure btnAllOrdersClick(Sender: TObject);
    procedure btnCancelAllOpenOrdersClick(Sender: TObject);
    procedure btnNewOrderClick(Sender: TObject);
    procedure btnSubscribeTickerClick(Sender: TObject);
    procedure btnTickerSnapshotClick(Sender: TObject);
    procedure wsclientConnect(Connection: TsgcWSConnection);
    procedure wsclientDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure wsclientException(Connection: TsgcWSConnection; E: Exception);
    procedure wsclientMessage(Connection: TsgcWSConnection; const Text: string);
  private
    procedure DoBinanceAPI;
    procedure DoLog(const aText: string);
  public
    { Public declarations }
  end;

var
  FRMSGCBinanceTradeFutures: TFRMSGCBinanceTradeFutures;

implementation

{$R *.dfm}

procedure TFRMSGCBinanceTradeFutures.FormCreate(Sender: TObject);
begin
  wsclient.Active := False;
end;

procedure TFRMSGCBinanceTradeFutures.binancefutBinanceHTTPException(Sender: TObject; E: Exception);
begin
  DoLog(E.Message);
end;

procedure TFRMSGCBinanceTradeFutures.btnAllOrdersClick(Sender: TObject);
begin
  DoBinanceAPI;

  DoLog(binancefut.REST_API.GetAllOrders(txtSymbol.Text));
end;

procedure TFRMSGCBinanceTradeFutures.btnCancelAllOpenOrdersClick(Sender: TObject);
begin
  DoBinanceAPI;

  DoLog(binancefut.REST_API.CancelAllOpenOrders(txtSymbol.Text));
end;

procedure TFRMSGCBinanceTradeFutures.btnNewOrderClick(Sender: TObject);
var
  vFS: TFormatSettings;
begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';

  DoBinanceAPI;

  case cboOrderType.ItemIndex of
    0:
      DoLog(binancefut.REST_API.NewOrder(txtSymbol.Text, cboSide.Text, '',
        cboOrderType.Text, '', StrToFloat(txtQuantity.Text, vFS)));
    1:
      DoLog(binancefut.REST_API.NewOrder(txtSymbol.Text, cboSide.Text, '',
        cboOrderType.Text, 'GTC', StrToFloat(txtQuantity.Text, vFS), 'false',
        StrToFloat(txtPrice.Text, vFS)));
  end;
end;

procedure TFRMSGCBinanceTradeFutures.btnSubscribeTickerClick(Sender: TObject);
begin
  if not wsclient.Active then
  begin
    wsClient.Connect;
    binancefut.SubscribeTicker(LowerCase(txtSymbol.Text));
    btnSubscribeTicker.Caption := 'Unsubscribe Ticker';
  end
  else
    btnSubscribeTicker.Caption := 'Subscribe Ticker';
end;

procedure TFRMSGCBinanceTradeFutures.btnTickerSnapshotClick(Sender: TObject);
begin
  DoLog(binancefut.REST_API.GetPriceTicker(txtSymbol.Text));
end;

procedure TFRMSGCBinanceTradeFutures.DoBinanceAPI;
begin
  binancefut.Binance.ApiKey := txtApiKey.Text;
  binancefut.Binance.ApiSecret := txtApiSecret.Text;
end;

procedure TFRMSGCBinanceTradeFutures.DoLog(const aText: string);
begin
  Memo1.Lines.Add(aText);
end;

procedure TFRMSGCBinanceTradeFutures.wsclientConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;

procedure TFRMSGCBinanceTradeFutures.wsclientDisconnect(Connection: TsgcWSConnection;
  Code: Integer);
begin
  DoLog('#disconnected');
end;

procedure TFRMSGCBinanceTradeFutures.wsclientException(Connection: TsgcWSConnection; E: Exception);
begin
  DoLog('#exception: ' + E.Message);
end;

procedure TFRMSGCBinanceTradeFutures.wsclientMessage(Connection: TsgcWSConnection;
  const Text: string);
begin
  DoLog(Text);
end;

end.
```

