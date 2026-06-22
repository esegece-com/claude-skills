# TsgcWSAPI_Bybit - Example

Usage of `TsgcWSAPI_Bybit` extracted from the **05.Crypto/14.Bybit** demo. See the full project for context.

API reference: [TsgcWSAPI_Bybit](../reference/api/TsgcWSAPI_Bybit.md)
Source demo: `05.Crypto/14.Bybit` (file `uBybit.pas`)

```pascal
procedure TfrmWebSocketClient.btnBybitSubscribeExecutionClick(Sender: TObject);
  begin
  Bybit.SubscribeExecution;
  end;

procedure TfrmWebSocketClient.btnBybitSubscribeKLineClick(Sender: TObject);
  begin
  Bybit.SubscribeKLine(txtBybitSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnBybitSubscribeOrderBookClick(Sender: TObject);
  begin
  Bybit.SubscribeOrderBook(txtBybitSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnBybitSubscribeOrderClick(Sender: TObject);
  begin
  Bybit.SubscribeOrder;
  end;

procedure TfrmWebSocketClient.btnBybitSubscribePositionClick(Sender: TObject);
  begin
  Bybit.SubscribePosition;
  end;

procedure TfrmWebSocketClient.btnBybitSubscribeTickersClick(Sender: TObject);
  begin
  Bybit.SubscribeTicker(txtBybitSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnBybitSubscribeTradeClick(Sender: TObject);
  begin
  Bybit.SubscribeTrade(txtBybitSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnBybitUnSubscribeKLineClick(Sender: TObject);
  begin
  Bybit.UnSubscribeKLine(txtBybitSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnBybitUnSubscribeOrderClick(Sender: TObject);
  begin
  Bybit.UnSubscribeOrder;
  end;

procedure TfrmWebSocketClient.btnBybitUnSubscribePositionClick(Sender: TObject);
  begin
  Bybit.UnSubscribePosition;
  end;

procedure TfrmWebSocketClient.btnBybitUnSubscribeTickersClick(Sender: TObject);
  begin
  Bybit.UnSubscribeTicker(txtBybitSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnBybitUnSubscribeTradeClick(Sender: TObject);
  begin
  Bybit.UnSubscribeTrade(txtBybitSymbol.Text);
  end;

```

