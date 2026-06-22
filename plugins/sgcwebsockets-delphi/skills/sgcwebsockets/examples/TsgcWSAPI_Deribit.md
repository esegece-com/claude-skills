# TsgcWSAPI_Deribit - Example

Usage of `TsgcWSAPI_Deribit` extracted from the **05.Crypto/18.Deribit** demo. See the full project for context.

API reference: [TsgcWSAPI_Deribit](../reference/api/TsgcWSAPI_Deribit.md)
Source demo: `05.Crypto/18.Deribit` (file `uDeribit.pas`)

```pascal
procedure TfrmWebSocketClient.FormCreate(Sender: TObject);
  begin
  Deribit.Client := WSClient;
  
  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
  end;

procedure TfrmWebSocketClient.btnDeribitSubscribeTickerClick(Sender: TObject);
  begin
  Deribit.SubscribeTicker(txtDeribitInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnDeribitUnSubscribeTickerClick(Sender: TObject);
  begin
  Deribit.UnSubscribeTicker(txtDeribitInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnDeribitSubscribeTradesClick(Sender: TObject);
  begin
  Deribit.SubscribeTrades(txtDeribitInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnDeribitUnSubscribeTradesClick(Sender: TObject);
  begin
  Deribit.UnSubscribeTrades(txtDeribitInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnDeribitSubscribeOrderBookClick(Sender: TObject);
  begin
  Deribit.SubscribeOrderBook(txtDeribitInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnDeribitSubscribeCandleClick(Sender: TObject);
  begin
  Deribit.SubscribeCandle(txtDeribitInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnDeribitUnSubscribeCandleClick(Sender: TObject);
  begin
  Deribit.UnSubscribeCandle(txtDeribitInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnDeribitSubscribePerpetualClick(Sender: TObject);
  begin
  Deribit.SubscribePerpetual(txtDeribitInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnDeribitSubscribeOrdersClick(Sender: TObject);
  begin
  Deribit.SubscribeOrders(txtDeribitInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnDeribitUnSubscribeOrdersClick(Sender: TObject);
  begin
  Deribit.UnSubscribeOrders(txtDeribitInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnDeribitSubscribePositionsClick(Sender: TObject);
```

