# TsgcWSAPI_Bitget - Example

Usage of `TsgcWSAPI_Bitget` extracted from the **05.Crypto/16.Bitget** demo. See the full project for context.

API reference: [TsgcWSAPI_Bitget](../reference/api/TsgcWSAPI_Bitget.md)
Source demo: `05.Crypto/16.Bitget` (file `uBitget.pas`)

```pascal
procedure TfrmWebSocketClient.FormCreate(Sender: TObject);
  begin
  Bitget.Client := WSClient;
  
  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
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
```

