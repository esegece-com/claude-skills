# TsgcWSAPI_Kraken - Example

Usage of `TsgcWSAPI_Kraken` extracted from the **05.Crypto/08.Kraken** demo. See the full project for context.

API reference: [TsgcWSAPI_Kraken](../reference/api/TsgcWSAPI_Kraken.md)
Source demo: `05.Crypto/08.Kraken` (file `uKraken.pas`)

```pascal
procedure TfrmWebSocketClient.btnKrakenCancelOrderClick(Sender: TObject);
  begin
  KRAKEN.CancelOrder(txtKrakenOrderId.Text);
  end;

procedure TfrmWebSocketClient.btnKrakenGetAccountBalanceClick(Sender: TObject);
  begin
  DoLog(KRAKEN.REST_API.GetAccountBalance);
  end;

procedure TfrmWebSocketClient.btnKrakenGetAssetsClick(Sender: TObject);
  begin
  DoLog(KRAKEN.REST_API.GetAssets);
  end;

procedure TfrmWebSocketClient.btnKrakenGetAssetsPairsClick(Sender: TObject);
  begin
  DoLog(KRAKEN.REST_API.GetAssetPairs([txtKrakenRESTPair.Text]));
  end;

procedure TfrmWebSocketClient.btnKrakenGetClosedOrdersClick(Sender: TObject);
  begin
  DoLog(KRAKEN.REST_API.GetClosedOrders());
  end;

procedure TfrmWebSocketClient.btnKrakenGetLedgersClick(Sender: TObject);
  begin
  DoLog(KRAKEN.REST_API.GetLedgers);
  end;

procedure TfrmWebSocketClient.btnKrakenGetServerTimeClick(Sender: TObject);
  begin
  DoLog(KRAKEN.REST_API.GetServerTime);
  end;

procedure TfrmWebSocketClient.btnKrakenGetTickerClick(Sender: TObject);
  begin
  DoLog(KRAKEN.REST_API.GetTicker([txtKrakenRESTPair.Text]));
  end;

procedure TfrmWebSocketClient.btnKrakenSubscribeAllClick(Sender: TObject);
  begin
  KRAKEN.SubscribeAll([txtKrakenPair.Text]);
  end;

procedure TfrmWebSocketClient.btnKrakenSubscribeOHLCClick(Sender: TObject);
  begin
  KRAKEN.SubscribeOHLC([txtKrakenPair.Text],
  TsgcWSKrakenInterval(cboKrakenInterval.itemIndex));
  end;

procedure TfrmWebSocketClient.btnKrakenSubscribeTickerClick(Sender: TObject);
  begin
  KRAKEN.SubscribeTicker([txtKrakenPair.Text]);
  end;

procedure TfrmWebSocketClient.btnKrakenSubscribeTradeClick(Sender: TObject);
  begin
  KRAKEN.SubscribeTrade([txtKrakenPair.Text]);
  end;
```

