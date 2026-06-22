# TsgcWSAPI_GateIO - Example

Usage of `TsgcWSAPI_GateIO` extracted from the **05.Crypto/17.GateIO** demo. See the full project for context.

API reference: [TsgcWSAPI_GateIO](../reference/api/TsgcWSAPI_GateIO.md)
Source demo: `05.Crypto/17.GateIO` (file `uGateIO.pas`)

```pascal
procedure TfrmWebSocketClient.FormCreate(Sender: TObject);
  begin
  GateIO.Client := WSClient;
  
  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
  end;

procedure TfrmWebSocketClient.btnGateIOSubscribeTickerClick(Sender: TObject);
  begin
  GateIO.SubscribeTicker(txtGateIOSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnGateIOUnSubscribeTickerClick(Sender: TObject);
  begin
  GateIO.UnSubscribeTicker(txtGateIOSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnGateIOSubscribeTradesClick(Sender: TObject);
  begin
  GateIO.SubscribeTrades(txtGateIOSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnGateIOUnSubscribeTradesClick(Sender: TObject);
  begin
  GateIO.UnSubscribeTrades(txtGateIOSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnGateIOSubscribeOrdersClick(Sender: TObject);
  begin
  GateIO.SubscribeOrders(txtGateIOSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnGateIOUnSubscribeOrdersClick(Sender: TObject);
  begin
  GateIO.UnSubscribeOrders(txtGateIOSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnGateIOSubscribeBalancesClick(Sender: TObject);
  begin
  GateIO.SubscribeBalances;
  end;

procedure TfrmWebSocketClient.btnGateIOPingClick(Sender: TObject);
  begin
  GateIO.Ping;
  end;

procedure TfrmWebSocketClient.btnGateIORESTCurrencyPairsClick(Sender: TObject);
  begin
  DoLog(GateIO.REST_API.GetCurrencyPairs);
  end;

procedure TfrmWebSocketClient.btnGateIORESTTickersClick(Sender: TObject);
  begin
  DoLog(GateIO.REST_API.GetTickers(txtGateIOSymbol.Text));
  end;

procedure TfrmWebSocketClient.btnGateIORESTOrderBookClick(Sender: TObject);
```

