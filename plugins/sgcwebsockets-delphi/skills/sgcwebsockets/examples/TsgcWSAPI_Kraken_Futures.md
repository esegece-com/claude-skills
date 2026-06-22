# TsgcWSAPI_Kraken_Futures - Example

Usage of `TsgcWSAPI_Kraken_Futures` extracted from the **05.Crypto/08.Kraken** demo. See the full project for context.

API reference: [TsgcWSAPI_Kraken_Futures](../reference/api/TsgcWSAPI_Kraken_Futures.md)
Source demo: `05.Crypto/08.Kraken` (file `uKraken.pas`)

```pascal
procedure TfrmWebSocketClient.btnKrakenFuturesMarketOrderClick(Sender: TObject);
  var
  vSide: TsgcHTTPKrakenFuturesOrderSide;
  begin
  if cboKrakenFuturesMarketOrderSide.itemIndex = 0 then
  vSide := kosfBuy
  else
  vSide := kosfSell;
  
  DoLog(KRAKEN_FUTURES.REST_API.SendMarketOrder(vSide, txtKrakenRESTPair.Text,
  StrToInt(txtKrakenFuturesMarketOrderSize.Text)));
  end;

procedure TfrmWebSocketClient.btnKrakenFuturesLimitOrderClick(Sender: TObject);
  var
  vSide: TsgcHTTPKrakenFuturesOrderSide;
  vFS: TFormatSettings;
  begin
  vFS.DecimalSeparator := '.';
  vFS.ThousandSeparator := ',';
  
  if cboKrakenFuturesLimitOrderSide.itemIndex = 0 then
  vSide := kosfBuy
  else
  vSide := kosfSell;
  
  DoLog(KRAKEN_FUTURES.REST_API.SendLimitOrder(vSide, txtKrakenRESTPair.Text,
  StrToInt(txtKrakenFuturesLimitOrderSize.Text),
  StrToFloat(txtKrakenFuturesLimitOrderPrice.Text, vFS)));
  end;

procedure TfrmWebSocketClient.chkKrakenFuturesDemoClick(Sender: TObject);
  begin
  KRAKEN_FUTURES.KRAKEN.Demo := chkKrakenFuturesDemo.Checked;
  if chkKrakenFuturesDemo.Checked then
  txtHost.Text := 'demo-futures.kraken.com'
  else
  txtHost.Text := 'futures.kraken.com';
  end;

KRAKEN_FUTURES.Client := WSClient;
KRAKEN_FUTURES.KRAKEN.ApiKey := txtKrakenApiKey.Text;
KRAKEN_FUTURES.KRAKEN.ApiSecret := txtKrakenApiSecret.Text;
procedure TfrmWebSocketClient.txtKrakenApiKeyChange(Sender: TObject);
  begin
  KRAKEN.KRAKEN.ApiKey := txtKrakenApiKey.Text;
  KRAKEN_FUTURES.KRAKEN.ApiKey := txtKrakenApiKey.Text;
  end;

procedure TfrmWebSocketClient.txtKrakenApiSecretChange(Sender: TObject);
  begin
  KRAKEN.KRAKEN.ApiSecret := txtKrakenApiSecret.Text;
  KRAKEN_FUTURES.KRAKEN.ApiSecret := txtKrakenApiSecret.Text;
  end;

KRAKEN_FUTURES.Client := nil;
```

