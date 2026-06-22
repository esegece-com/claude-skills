# TsgcWSAPI_Coinbase - Example

Usage of `TsgcWSAPI_Coinbase` extracted from the **05.Crypto/09.Coinbase** demo. See the full project for context.

API reference: [TsgcWSAPI_Coinbase](../reference/api/TsgcWSAPI_Coinbase.md)
Source demo: `05.Crypto/09.Coinbase` (file `uCoinbase.pas`)

```pascal
procedure TfrmWebSocketClient.btnCoinbaseGetOrderBookClick(Sender: TObject);
  begin
  DoLog(COINBASE.REST_API.GetPublicProductBook(txtCoinbaseProductId.Text));
  end;

procedure TfrmWebSocketClient.btnCoinbaseGetProductClick(Sender: TObject);
  begin
  DoLog(COINBASE.REST_API.GetPublicProduct(txtCoinbaseProductId.Text));
  end;

procedure TfrmWebSocketClient.btnCoinbaseListOrdersClick(Sender: TObject);
  begin
  DoLog(COINBASE.REST_API.ListOrders);
  end;

procedure TfrmWebSocketClient.btnCoinbaseGetProductsClick(Sender: TObject);
  begin
  DoLog(COINBASE.REST_API.GetPublicProducts);
  end;

procedure TfrmWebSocketClient.btnCoinbaseGetCandlesClick(Sender: TObject);
  begin
  DoLog(COINBASE.REST_API.GetPublicProductCandles(txtCoinbaseProductId.Text,
  Trunc(Now), Now, cgr5m));
  end;

procedure TfrmWebSocketClient.btnCoinbaseGetTradesClick(Sender: TObject);
  begin
  DoLog(COINBASE.REST_API.GetTrades(txtCoinbaseProductId.Text));
  end;

procedure TfrmWebSocketClient.btnCoinbaseLimitOrderClick(Sender: TObject);
  var
  vSide: TsgcHTTPCoinbaseOrderSide;
  vFS: TFormatSettings;
  begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';
  
  if cboCoinbaseLimitOrderSide.itemIndex = 0 then
  vSide := coisBuy
  else
  vSide := coisSell;
  
  DoLog(COINBASE.REST_API.PlaceLimitOrder(vSide, txtCoinbaseProductId.Text,
  StrToFloat(txtCoinbaseLimitOrderAmount.Text, vFS), 0,
  StrToFloat(txtCoinbaseLimitOrderPrice.Text, vFS)));
  end;

procedure TfrmWebSocketClient.btnCoinbaseListProductsClick(Sender: TObject);
  begin
  DoLog(COINBASE.REST_API.ListProducts);
  end;

procedure TfrmWebSocketClient.btnCoinbaseGetTransactionSummaryClick(Sender: TObject);
  begin
  DoLog(COINBASE.REST_API.GetTransactionSummary);
  end;

procedure TfrmWebSocketClient.btnCoinbaseListPortfoliosClick(Sender: TObject);
```

