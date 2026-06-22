# TsgcWSAPI_Kucoin - Example

Usage of `TsgcWSAPI_Kucoin` extracted from the **05.Crypto/11.Kucoin** demo. See the full project for context.

API reference: [TsgcWSAPI_Kucoin](../reference/api/TsgcWSAPI_Kucoin.md)
Source demo: `05.Crypto/11.Kucoin` (file `uKucoin.pas`)

```pascal
procedure TfrmWebSocketClient.btnKucoinFutGetTickerClick(Sender: TObject);
  begin
  DoLog(KUCOINFUT.REST_API.GetTicker(txtKucoinSymbol.Text));
  end;

procedure TfrmWebSocketClient.btnKucoinFutGetTradeHistoryClick(Sender: TObject);
  begin
  DoLog(KUCOINFUT.REST_API.GetTradeHistory(txtKucoinSymbol.Text));
  end;

procedure TfrmWebSocketClient.btnKucoinFutServiceStatusClick(Sender: TObject);
  begin
  DoLog(KUCOINFUT.REST_API.GetServiceStatus);
  end;

procedure TfrmWebSocketClient.btnKucoinFuturesLimitOrderClick(Sender: TObject);
  var
  vSide: TsgcHTTPKucoinOrderSide;
  begin
  if cboKucoinFuturesMarketOrderSide.itemIndex = 0 then
  vSide := kosBuy
  else
  vSide := kosSell;
  
  DoLog(KUCOINFUT.REST_API.PlaceMarketOrder(vSide, txtKucoinSymbol.Text,
  StrToInt(txtKucoinFuturesMarketSize.Text)));
  end;

procedure TfrmWebSocketClient.btnKucoinFuturesMarketOrderClick(Sender: TObject);
  var
  vSide: TsgcHTTPKucoinOrderSide;
  vFS: TFormatSettings;
  begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';
  
  if cboKucoinFuturesLimitOrderSide.itemIndex = 0 then
  vSide := kosBuy
  else
  vSide := kosSell;
  
  DoLog(KUCOINFUT.REST_API.PlaceLimitOrder(vSide, txtKucoinSymbol.Text,
  StrToInt(txtKucoinFuturesLimitSize.Text),
  StrToFloat(txtKucoinFuturesLimitPrice.Text, vFS)));
  end;

procedure TfrmWebSocketClient.btnKucoinSubscribeLevel1Click(Sender: TObject);
  begin
  KUCOIN.SubscribeLevel1(txtKucoinSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnKucoinUnSubscribeLevel1Click(Sender: TObject);
  begin
  KUCOIN.UnSubscribeLevel1(txtKucoinSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnKucoinGetDepositAddressesClick(
  Sender: TObject);
  begin
  DoLog(KUCOIN.REST_API.GetDepositAddresses(txtKucoinSymbol.Text));
```

