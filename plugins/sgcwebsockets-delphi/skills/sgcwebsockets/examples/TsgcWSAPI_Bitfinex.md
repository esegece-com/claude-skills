# TsgcWSAPI_Bitfinex - Example

Usage of `TsgcWSAPI_Bitfinex` extracted from the **05.Crypto/21.Bitfinex** demo. See the full project for context.

API reference: [TsgcWSAPI_Bitfinex](../reference/api/TsgcWSAPI_Bitfinex.md)
Source demo: `05.Crypto/21.Bitfinex` (file `uBitfinex.pas`)

```pascal
procedure TfrmWebSocketClient.BITFINEXBitfinexConnect(Sender: TObject;
  Version: String);
  begin
  DoLog('#bitfinex connected, version: ' + Version);
  end;

procedure TfrmWebSocketClient.btnSubscribeTickerClick(Sender: TObject);
  begin
  BITFINEX.SubscribeTicker(txtSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnSubscribeTradesClick(Sender: TObject);
  begin
  BITFINEX.SubscribeTrades(txtSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnSubscribeOrderBookClick(Sender: TObject);
  begin
  BITFINEX.SubscribeOrderBook(txtSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnSubscribeRawOrderBookClick(Sender: TObject);
  begin
  BITFINEX.SubscribeRawOrderBook(txtSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnSubscribeCandlesClick(Sender: TObject);
  begin
  BITFINEX.SubscribeCandles(txtCandleKey.Text);
  end;

procedure TfrmWebSocketClient.btnUnsubscribeClick(Sender: TObject);
  var
  vChanId: Integer;
  begin
  vChanId := StrToIntDef(txtUnsubChanId.Text, 0);
  BITFINEX.UnSubscribeTicker(vChanId);
  end;

procedure TfrmWebSocketClient.btnPingClick(Sender: TObject);
  begin
  BITFINEX.Ping;
  end;

procedure TfrmWebSocketClient.btnConfigDecStringsClick(Sender: TObject);
  begin
  BITFINEX.Configuration(8);
  end;

procedure TfrmWebSocketClient.btnConfigTimeStringsClick(Sender: TObject);
  begin
  BITFINEX.Configuration(32);
  end;

procedure TfrmWebSocketClient.btnConfigSequencingClick(Sender: TObject);
  begin
  BITFINEX.Configuration(65536);
  end;

procedure TfrmWebSocketClient.btnConfigChecksumClick(Sender: TObject);
```

