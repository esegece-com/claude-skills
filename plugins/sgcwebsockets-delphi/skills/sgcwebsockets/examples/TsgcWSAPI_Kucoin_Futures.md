# TsgcWSAPI_Kucoin_Futures - Example

Usage of `TsgcWSAPI_Kucoin_Futures` extracted from the **05.Crypto/11.Kucoin** demo. See the full project for context.

API reference: [TsgcWSAPI_Kucoin_Futures](../reference/api/TsgcWSAPI_Kucoin_Futures.md)
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

procedure TfrmWebSocketClient.Button62Click(Sender: TObject);
  begin
  DoLog(KUCOINFUT.REST_API.GetServerTime);
  end;

procedure TfrmWebSocketClient.chkKucoinSandBoxClick(Sender: TObject);
  begin
  KUCOIN.Kucoin.SandBox := chkKucoinSandBox.Checked;
  KUCOINFUT.Kucoin.SandBox := chkKucoinSandBox.Checked;
  
  tabKUCOINShow(nil);
  end;

KUCOINFUT.Client := WSClient;
```

