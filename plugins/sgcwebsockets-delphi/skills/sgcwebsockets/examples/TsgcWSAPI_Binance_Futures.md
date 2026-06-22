# TsgcWSAPI_Binance_Futures - Example

Usage of `TsgcWSAPI_Binance_Futures` extracted from the **02.WebSocket_Protocols/09.Binance_Trade_Futures** demo. See the full project for context.

API reference: [TsgcWSAPI_Binance_Futures](../reference/api/TsgcWSAPI_Binance_Futures.md)
Source demo: `02.WebSocket_Protocols/09.Binance_Trade_Futures` (file `FsgcBinanceTradeFutures.pas`)

```pascal
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

binancefut.Binance.ApiKey := txtApiKey.Text;
binancefut.Binance.ApiSecret := txtApiSecret.Text;
```

