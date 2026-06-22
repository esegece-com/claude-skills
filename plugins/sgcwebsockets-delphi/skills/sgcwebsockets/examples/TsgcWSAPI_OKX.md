# TsgcWSAPI_OKX - Example

Usage of `TsgcWSAPI_OKX` extracted from the **05.Crypto/12.OKX** demo. See the full project for context.

API reference: [TsgcWSAPI_OKX](../reference/api/TsgcWSAPI_OKX.md)
Source demo: `05.Crypto/12.OKX` (file `uOKX.pas`)

```pascal
procedure TfrmWebSocketClient.btnOkxSubscribeAccountClick(Sender: TObject);
  begin
  OKX.SubscribeAccount;
  end;

procedure TfrmWebSocketClient.btnOkxSubscribeInstrumentsClick(Sender: TObject);
  begin
  OKX.SubscribeInstruments;
  end;

procedure TfrmWebSocketClient.btnOkxSubscribeTickerClick(Sender: TObject);
  begin
  OKX.SubscribeTicker(txtOkxInstId.Text);
  end;

procedure TfrmWebSocketClient.btnOkxUnSubscribeTickerClick(Sender: TObject);
  begin
  OKX.UnSubscribeTicker(txtOkxInstId.Text);
  end;

procedure TfrmWebSocketClient.btnOkxSubscribeCandlesticksClick(Sender: TObject);
  begin
  OKX.SubscribeCandlestick(txtOkxInstId.Text);
  end;

procedure TfrmWebSocketClient.btnOkxSubscribeTradeOrdersClick(Sender: TObject);
  begin
  OKX.SubscribeTrades(txtOkxInstId.Text);
  end;

procedure TfrmWebSocketClient.btnOkxUnSubscribeOrderBookClick(Sender: TObject);
  begin
  OKX.UnSubscribeOrderBook(txtOkxInstId.Text);
  end;

procedure TfrmWebSocketClient.btnOkxSubscribeOrderBookClick(Sender: TObject);
  begin
  OKX.SubscribeOrderBook(txtOkxInstId.Text);
  end;

procedure TfrmWebSocketClient.btnOkxSubscribeOrdersClick(Sender: TObject);
  begin
  OKX.SubscribeOrders;
  end;

procedure TfrmWebSocketClient.btnOkxSubscribeStatusClick(Sender: TObject);
  begin
  OKX.SubscribeStatus;
  end;

procedure TfrmWebSocketClient.btnOkxUnSubscribeAccountClick(Sender: TObject);
  begin
  OKX.UnSubscribeAccount;
  end;

procedure TfrmWebSocketClient.btnOkxUnSubscribeOrdersClick(Sender: TObject);
  begin
  OKX.UnSubscribeOrders;
  end;

```

