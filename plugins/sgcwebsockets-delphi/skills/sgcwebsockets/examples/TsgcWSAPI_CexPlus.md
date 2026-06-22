# TsgcWSAPI_CexPlus - Example

Usage of `TsgcWSAPI_CexPlus` extracted from the **05.Crypto/05.CexPlus** demo. See the full project for context.

API reference: [TsgcWSAPI_CexPlus](../reference/api/TsgcWSAPI_CexPlus.md)
Source demo: `05.Crypto/05.CexPlus` (file `uCexPlus.pas`)

```pascal
procedure TfrmWebSocketClient.btnCexPlusAccountStatusClick(Sender: TObject);
  begin
  CEX_PLUS.GetAccountStatus;
  end;

procedure TfrmWebSocketClient.btnCexPlusCancelAllOrdersClick(Sender: TObject);
  begin
  CEX_PLUS.CancelAllOrders;
  end;

procedure TfrmWebSocketClient.btnCexPlusSubscribeTradeClick(Sender: TObject);
  begin
  CEX_PLUS.SubscribeTrade(txtCexPlusPair.Text);
  end;

procedure TfrmWebSocketClient.btnCexPlusUnSubscribeTradeClick(Sender: TObject);
  begin
  CEX_PLUS.UnSubscribeTrade(txtCexPlusPair.Text);
  end;

procedure TfrmWebSocketClient.btnCexPlusGetCandlesClick(Sender: TObject);
  begin
  CEX_PLUS.GetCandles(txtCexPlusPair.Text, cxpdtBestAsk,
  TsgcWSCexPlusResolution(cboCexPlusResolution.itemIndex),
  IncDay(Now, -1), 0, 1000);
  end;

procedure TfrmWebSocketClient.btnCexPlusGetOrdersClick(Sender: TObject);
  begin
  CEX_PLUS.GetOrders;
  end;

procedure TfrmWebSocketClient.btnCexPlusGetWalletBalanceClick(Sender: TObject);
  begin
  CEX_PLUS.GetWalletBalance;
  end;

procedure TfrmWebSocketClient.btnCexPlusSubscribeAccountEventsClick(Sender: TObject);
  begin
  CEX_PLUS.SubscribeAccountEvents;
  end;

procedure TfrmWebSocketClient.btnCexPlusUnSubscribeAccountEventsClick(Sender: TObject);
  begin
  CEX_PLUS.UnSubscribeAccountEvents;
  end;

CEX_PLUS.Client := WSClient;
procedure TfrmWebSocketClient.txtCexPlusApiKeyChange(Sender: TObject);
  begin
  CEX_PLUS.CexPlus.ApiKey := txtCexPlusApiKey.Text;
  DoServerCEX_PLUS;
  end;

procedure TfrmWebSocketClient.txtCexPlusApiSecretChange(Sender: TObject);
  begin
  CEX_PLUS.CexPlus.ApiSecret := txtCexPlusApiSecret.Text;
  end;

CEX_PLUS.Client := nil;
```

