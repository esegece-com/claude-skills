# TsgcWSAPI_XTB - Example

Usage of `TsgcWSAPI_XTB` extracted from the **05.Crypto/13.XTB** demo. See the full project for context.

API reference: [TsgcWSAPI_XTB](../reference/api/TsgcWSAPI_XTB.md)
Source demo: `05.Crypto/13.XTB` (file `uXTB.pas`)

```pascal
procedure TfrmWebSocketClient.btnSubscribeTradesClick(Sender: TObject);
  begin
  XTB.SubscribeTrades;
  end;

procedure TfrmWebSocketClient.btnUnsubscribeTradesClick(Sender: TObject);
  begin
  XTB.UnSubscribeTrades;
  end;

procedure TfrmWebSocketClient.btnXTBGetAllSymbolsClick(Sender: TObject);
  begin
  XTB.GetAllSymbols;
  end;

procedure TfrmWebSocketClient.btnXTBGetCurrentUserDataClick(Sender: TObject);
  begin
  XTB.GetCurrentUserData;
  end;

procedure TfrmWebSocketClient.btnXTBGetServerTimeClick(Sender: TObject);
  begin
  XTB.GetServerTime;
  end;

procedure TfrmWebSocketClient.btnXTBGetSymbolClick(Sender: TObject);
  begin
  XTB.GetSymbol(txtXTBSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnXTBGetTickPricesClick(Sender: TObject);
  begin
  XTB.GetTickPrices(txtXTBSymbol.Text, 0, Trunc(Now));
  end;

procedure TfrmWebSocketClient.btnXTBGetTradesClick(Sender: TObject);
  begin
  XTB.GetTrades;
  end;

procedure TfrmWebSocketClient.btnXTBGetTradingHoursClick(Sender: TObject);
  begin
  XTB.GetTradingHours(txtXTBSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnXTBGetVersionClick(Sender: TObject);
  begin
  XTB.GetVersion;
  end;

procedure TfrmWebSocketClient.btnXTBLimitOrderClick(Sender: TObject);
  var
  vFS: TFormatSettings;
  begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';
  
  case cboXTBMarketSide.itemIndex of
  0:
  XTB.TradeTransaction(xtbcBuyLimit, '', IncDay(Now, 1), 0, 0,
```

