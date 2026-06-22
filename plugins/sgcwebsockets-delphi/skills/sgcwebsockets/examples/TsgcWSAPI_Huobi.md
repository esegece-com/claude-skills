# TsgcWSAPI_Huobi - Example

Usage of `TsgcWSAPI_Huobi` extracted from the **05.Crypto/03.Huobi** demo. See the full project for context.

API reference: [TsgcWSAPI_Huobi](../reference/api/TsgcWSAPI_Huobi.md)
Source demo: `05.Crypto/03.Huobi` (file `uHuobi.pas`)

```pascal
procedure TfrmWebSocketClient.btnSubscribeHuobiKLineClick(Sender: TObject);
  begin
  HUOBI.SubscribeKLine(txtHuobiSymbol.Text,
  TsgcWSHuobiPeriods(cboHuobiPeriods.itemIndex));
  end;

procedure TfrmWebSocketClient.btnUnSubscribeHuobiKLineClick(Sender: TObject);
  begin
  HUOBI.UnSubscribeKLine(txtHuobiSymbol.Text,
  TsgcWSHuobiPeriods(cboHuobiPeriods.itemIndex));
  end;

procedure TfrmWebSocketClient.btnSubscribeHuobiMBPClick(Sender: TObject);
  begin
  HUOBI.SubscribeMarketByPrice(txtHuobiSymbol.Text,
  TsgcWSHuobiLevels(cboHuobiMBPLevels.ItemIndex));
  end;

procedure TfrmWebSocketClient.btnUnSubscribeHuobiMBPClick(Sender: TObject);
  begin
  HUOBI.UnSubscribeMarketByPrice(txtHuobiSymbol.Text,
  TsgcWSHuobiLevels(cboHuobiMBPLevels.ItemIndex));
  end;

HUOBI.Client := WSClient;
procedure TfrmWebSocketClient.txtHuobiApiKeyChange(Sender: TObject);
  begin
  HUOBI.Huobi.ApiKey := txtHuobiApiKey.Text;
  DoServerHUOBI;
  end;

procedure TfrmWebSocketClient.txtHuobiApiSecretChange(Sender: TObject);
  begin
  HUOBI.Huobi.ApiSecret := txtHuobiApiSecret.Text;
  end;

HUOBI.Client := nil;
```

