# TsgcWSAPI_Cex - Example

Usage of `TsgcWSAPI_Cex` extracted from the **05.Crypto/04.Cex** demo. See the full project for context.

API reference: [TsgcWSAPI_Cex](../reference/api/TsgcWSAPI_Cex.md)
Source demo: `05.Crypto/04.Cex` (file `uCex.pas`)

```pascal
procedure TfrmWebSocketClient.btnCexSubscribeTickersClick(Sender: TObject);
  begin
  CEX.SubscribeTickers;
  end;

procedure TfrmWebSocketClient.btnCexAuthenticateClick(Sender: TObject);
  begin
  CEX.Cex.ApiKey := txtCexApiKey.Text;
  CEX.Cex.ApiSecret := txtCexApiSecret.Text;
  CEX.Authenticate;
  end;

procedure TfrmWebSocketClient.btnCexGetBalanceClick(Sender: TObject);
  begin
  CEX.GetBalance;
  end;

procedure TfrmWebSocketClient.btnCexGetTickerClick(Sender: TObject);
  begin
  CEX.GetTicker(txtCexSymbol1.Text, txtCexSymbol2.Text);
  end;

procedure TfrmWebSocketClient.btnCexSubscribeChartsClick(Sender: TObject);
  begin
  CEX.SubscribeChart(TsgcWSCexPeriods(cboCexPeriods.itemIndex),
  txtCexSymbol1.Text, txtCexSymbol2.Text);
  end;

procedure TfrmWebSocketClient.btnCexSubscribeOrderBookClick(Sender: TObject);
  begin
  CEX.SubscribeOrderBook(txtCexSymbol1.Text, txtCexSymbol2.Text);
  end;

procedure TfrmWebSocketClient.btnCexUnsubscribeOrderBookClick(Sender: TObject);
  begin
  CEX.UnSubscribeOrderBook(txtCexSymbol1.Text, txtCexSymbol2.Text);
  end;

procedure TfrmWebSocketClient.btnCexUnSubscribeTickersClick(Sender: TObject);
  begin
  CEX.UnSubscribeTickers;
  end;

procedure TfrmWebSocketClient.btnCexGetOpenOrdersClick(Sender: TObject);
  begin
  CEX.GetOpenOrders(txtCexSymbol1.Text, txtCexSymbol2.Text);
  end;

procedure TfrmWebSocketClient.btnCexGetArchivedOrdersClick(Sender: TObject);
  begin
  CEX.GetArchivedOrders(txtCexSymbol1.Text, txtCexSymbol2.Text);
  end;

procedure TfrmWebSocketClient.btnCexGetOpenPositionsClick(Sender: TObject);
  begin
  CEX.GetOpenPositions(txtCexSymbol1.Text, txtCexSymbol2.Text);
  end;

CEX.Client := WSClient;
CEX.Client := nil;
```

