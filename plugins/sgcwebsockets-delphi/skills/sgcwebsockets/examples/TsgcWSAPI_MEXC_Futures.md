# TsgcWSAPI_MEXC_Futures - Example

Usage of `TsgcWSAPI_MEXC_Futures` extracted from the **05.Crypto/15.MEXC** demo. See the full project for context.

API reference: [TsgcWSAPI_MEXC_Futures](../reference/api/TsgcWSAPI_MEXC_Futures.md)
Source demo: `05.Crypto/15.MEXC` (file `uMEXC.pas`)

```pascal
procedure TfrmWebSocketClient.btnMEXCFUT_SubscribeDepthClick(Sender: TObject);
  begin
  MEXCFUT.SubscribeDepth(txtMEXCSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnMEXCFUT_SubscribeKLineClick(Sender: TObject);
  begin
  MEXCFUT.SubscribeKLine(txtMEXCSymbol.Text, mexcKlineMin15);
  end;

procedure TfrmWebSocketClient.btnMEXCFUT_SubscribeTickerClick(Sender: TObject);
  begin
  MEXCFUT.SubscribeTicker(txtMEXCSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnMEXCFUT_UnSubscribeDepthClick(Sender: TObject);
  begin
  MEXCFUT.UnSubscribeDepth(txtMEXCSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnMEXCFUT_UnSubscribeKLineClick(Sender: TObject);
  begin
  MEXCFUT.UnSubscribeKLine(txtMEXCSymbol.Text, mexcKlineMin15);
  end;

procedure TfrmWebSocketClient.btnMEXCFUT_UnSubscribeTickerClick(Sender: TObject);
  begin
  MEXCFUT.UnSubscribeTicker(txtMEXCSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnMEXCFuturesDepthClick(Sender: TObject);
  begin
  DoLog(MEXCFUT.REST_API.GetDepth(txtMEXCSymbol.Text));
  end;

procedure TfrmWebSocketClient.btnMEXCFuturesDealsClick(Sender: TObject);
  begin
  DoLog(MEXCFUT.REST_API.GetDeals(txtMEXCSymbol.Text));
  end;

procedure TfrmWebSocketClient.btnMEXCFuturesKlinesClick(Sender: TObject);
  begin
  DoLog(MEXCFUT.REST_API.GetKlines(txtMEXCSymbol.Text, 'Min15'));
  end;

procedure TfrmWebSocketClient.btnMEXCFuturesIndexPriceClick(Sender: TObject);
  begin
  DoLog(MEXCFUT.REST_API.GetIndexPrice(txtMEXCSymbol.Text));
  end;

procedure TfrmWebSocketClient.btnMEXCFuturesAccountAssetsClick(
  Sender: TObject);
  begin
  DoLog(MEXCFUT.REST_API.GetAccountAssets);
  end;

procedure TfrmWebSocketClient.btnMEXCFuturesPositionListClick(Sender: TObject);
  begin
  DoLog(MEXCFUT.REST_API.GetPositionList);
  end;
```

