# TsgcWSAPI_CryptoCom - Example

Usage of `TsgcWSAPI_CryptoCom` extracted from the **05.Crypto/19.CryptoCom** demo. See the full project for context.

API reference: [TsgcWSAPI_CryptoCom](../reference/api/TsgcWSAPI_CryptoCom.md)
Source demo: `05.Crypto/19.CryptoCom` (file `uCryptoCom.pas`)

```pascal
procedure TfrmWebSocketClient.FormCreate(Sender: TObject);
  begin
  CryptoCom.Client := WSClient;
  
  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
  end;

procedure TfrmWebSocketClient.btnCryptoComSubscribeTickerClick(Sender: TObject);
  begin
  CryptoCom.SubscribeTicker(txtCryptoComInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnCryptoComUnSubscribeTickerClick(Sender: TObject);
  begin
  CryptoCom.UnSubscribeTicker(txtCryptoComInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnCryptoComSubscribeTradeClick(Sender: TObject);
  begin
  CryptoCom.SubscribeTrade(txtCryptoComInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnCryptoComUnSubscribeTradeClick(Sender: TObject);
  begin
  CryptoCom.UnSubscribeTrade(txtCryptoComInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnCryptoComSubscribeCandlestickClick(Sender: TObject);
  begin
  CryptoCom.SubscribeCandlestick(txtCryptoComInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnCryptoComUnSubscribeCandlestickClick(Sender: TObject);
  begin
  CryptoCom.UnSubscribeCandlestick(txtCryptoComInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnCryptoComSubscribeBookClick(Sender: TObject);
  begin
  CryptoCom.SubscribeBook(txtCryptoComInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnCryptoComUnSubscribeBookClick(Sender: TObject);
  begin
  CryptoCom.UnSubscribeBook(txtCryptoComInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnCryptoComSubscribeOrdersClick(Sender: TObject);
  begin
  CryptoCom.SubscribeOrders(txtCryptoComInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnCryptoComUnSubscribeOrdersClick(Sender: TObject);
  begin
  CryptoCom.UnSubscribeOrders(txtCryptoComInstrument.Text);
  end;

procedure TfrmWebSocketClient.btnCryptoComSubscribeUserTradesClick(Sender: TObject);
```

