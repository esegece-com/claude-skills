# TsgcWSAPI_ThreeCommas - Example

Usage of `TsgcWSAPI_ThreeCommas` extracted from the **05.Crypto/10.ThreeCommas** demo. See the full project for context.

API reference: [TsgcWSAPI_ThreeCommas](../reference/api/TsgcWSAPI_ThreeCommas.md)
Source demo: `05.Crypto/10.ThreeCommas` (file `uThreeCommas.pas`)

```pascal
procedure TfrmWebSocketClient.btnThreeComasSubscribeDealsClick(Sender: TObject);
  begin
  THREE_COMMAS.SubscribeDeals;
  end;

procedure TfrmWebSocketClient.btnThreeCommasGetAccountsClick(Sender: TObject);
  begin
  DoLog(THREE_COMMAS.REST_API.GetAccounts);
  end;

procedure TfrmWebSocketClient.btnThreeCommasGetBalancesClick(Sender: TObject);
  begin
  DoLog(THREE_COMMAS.REST_API.GetBalances
  (StrToInt(txtThreeCommasAccountId.Text)));
  end;

procedure TfrmWebSocketClient.btnThreeCommasGetMarketListClick(Sender: TObject);
  begin
  DoLog(THREE_COMMAS.REST_API.GetMarketList);
  end;

procedure TfrmWebSocketClient.btnThreeCommasMarketOrderClick(Sender: TObject);
  var
  vSide: TsgcHTTPThreeCommasOrderSide;
  vFS: TFormatSettings;
  begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';
  
  if cboThreeCommasMarketSide.itemIndex = 0 then
  vSide := os3cBuy
  else
  vSide := os3cSell;
  
  DoLog(THREE_COMMAS.REST_API.PlaceMarketOrder
  (StrToInt(txtThreeCommasAccountId.Text), vSide, txtThreeCommasPair.Text,
  StrToFloat(txtThreeCommasMarketSize.Text, vFS)));
  end;

procedure TfrmWebSocketClient.btnThreeCommasLimitOrderClick(Sender: TObject);
  var
  vSide: TsgcHTTPThreeCommasOrderSide;
  vFS: TFormatSettings;
  begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';
  
  if cboThreeCommasLimitSide.itemIndex = 0 then
  vSide := os3cBuy
  else
  vSide := os3cSell;
  
  DoLog(THREE_COMMAS.REST_API.PlaceLimitOrder
  (StrToInt(txtThreeCommasAccountId.Text), vSide, txtThreeCommasPair.Text,
  StrToFloat(txtThreeCommasLimitSize.Text, vFS),
  StrToFloat(txtThreeCommasLimitPrice.Text, vFS)));
  end;

procedure TfrmWebSocketClient.btnThreeCommasGetDCABotsClick(Sender: TObject);
  begin
```

