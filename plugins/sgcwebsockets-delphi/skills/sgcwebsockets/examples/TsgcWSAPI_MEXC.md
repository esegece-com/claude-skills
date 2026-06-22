# TsgcWSAPI_MEXC - Example

Usage of `TsgcWSAPI_MEXC` extracted from the **05.Crypto/15.MEXC** demo. See the full project for context.

API reference: [TsgcWSAPI_MEXC](../reference/api/TsgcWSAPI_MEXC.md)
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

procedure TfrmWebSocketClient.btnMEXC_SubscribeAccountDealsClick(Sender:
  TObject);
  begin
  MEXC.SubscribeAccountDeals;
  end;

procedure TfrmWebSocketClient.btnMEXC_SubscribeAccountOrdersClick(Sender:
  TObject);
  begin
  MEXC.SubscribeAccountOrders;
  end;

procedure TfrmWebSocketClient.btnMEXC_SubscribeAccountUpdateClick(Sender:
  TObject);
  begin
  MEXC.SubscribeAccountUpdate;
  end;

procedure TfrmWebSocketClient.btnMEXC_SubscribeKLineClick(Sender: TObject);
  begin
  MEXC.SubscribeKLine(txtMEXCSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnMEXC_SubscribeTradeClick(Sender: TObject);
  begin
  MEXC.SubscribeTrade(txtMEXCSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnMEXC_UnSubscribeAccountDealsClick(Sender:
  TObject);
```

