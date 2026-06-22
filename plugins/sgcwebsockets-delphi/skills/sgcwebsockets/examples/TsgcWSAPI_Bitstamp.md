# TsgcWSAPI_Bitstamp - Example

Usage of `TsgcWSAPI_Bitstamp` extracted from the **05.Crypto/02.Bitstamp** demo. See the full project for context.

API reference: [TsgcWSAPI_Bitstamp](../reference/api/TsgcWSAPI_Bitstamp.md)
Source demo: `05.Crypto/02.Bitstamp` (file `uBitstamp.pas`)

```pascal
procedure TfrmWebSocketClient.btnFullOrderBookBITSTAMPClick(Sender: TObject);
  begin
  BITSTAMP.SubscribeLiveFullOrderBook(txtBitstampCurrency.Text);
  end;

procedure TfrmWebSocketClient.btnLiveOrdersBITSTAMPClick(Sender: TObject);
  begin
  BITSTAMP.SubscribeLiveOrders(txtBitstampCurrency.Text);
  end;

procedure TfrmWebSocketClient.btnOrderBookBITSTAMPClick(Sender: TObject);
  begin
  BITSTAMP.SubscribeLiveOrderBook(txtBitstampCurrency.Text);
  end;

procedure TfrmWebSocketClient.btnTickerBITSTAMPClick(Sender: TObject);
  begin
  BITSTAMP.SubscribeLiveTicker(txtBitstampCurrency.Text);
  end;

procedure TfrmWebSocketClient.btnDetailOrderBookBITSTAMPClick(Sender: TObject);
  begin
  BITSTAMP.SubscribeLiveDetailOrderBook(txtBitstampCurrency.Text);
  end;

procedure TfrmWebSocketClient.btnBitstampAccountBalancesClick(Sender: TObject);
  begin
  DoLog(BITSTAMP.REST_API.GetAccountBalances);
  end;

procedure TfrmWebSocketClient.btnBitstampAllOpenOrdersClick(Sender: TObject);
  begin
  DoLog(BITSTAMP.REST_API.GetAllOpenOrders);
  end;

procedure TfrmWebSocketClient.btnBitstampCancelAllOrdersClick(Sender: TObject);
  begin
  DoLog(BITSTAMP.REST_API.CancelAllOrders);
  end;

procedure TfrmWebSocketClient.btnBitstampCurrenciesClick(Sender: TObject);
  begin
  DoLog(BITSTAMP.REST_API.GetCurrencies);
  end;

procedure TfrmWebSocketClient.btnBitstampEURUSDClick(Sender: TObject);
  begin
  DoLog(BITSTAMP.REST_API.GetEURUSDConversionRate);
  end;

procedure TfrmWebSocketClient.btnBitstampLimitOrderClick(Sender: TObject);
  begin
  if cboBitstampLimitSide.itemIndex = 0 then
  DoLog(BITSTAMP.REST_API.BuyLimitOrder(txtBitstampCurrency.Text,
  txtBitstampLimitAmount.Text, txtBitstampLimitPrice.Text))
  else
  DoLog(BITSTAMP.REST_API.SellLimitOrder(txtBitstampCurrency.Text,
  txtBitstampLimitAmount.Text, txtBitstampLimitPrice.Text));
  end;

```

