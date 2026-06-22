# TsgcWSAPI_Bitmex - Example

Usage of `TsgcWSAPI_Bitmex` extracted from the **05.Crypto/06.Bitmex** demo. See the full project for context.

API reference: [TsgcWSAPI_Bitmex](../reference/api/TsgcWSAPI_Bitmex.md)
Source demo: `05.Crypto/06.Bitmex` (file `uBitmex.pas`)

```pascal
procedure TfrmWebSocketClient.BITMEXBitmexAuthenticated(Sender: TObject);
  begin
  DoLog('#Bitmex Authenticated');
  end;

procedure TfrmWebSocketClient.BITMEXBitmexConnect(Sender: TObject;
  const aMessage: string);
  begin
  DoLog('#Bitmex Connected: ' + aMessage);
  end;

procedure TfrmWebSocketClient.BITMEXBitmexError(Sender: TObject;
  const aMessage: string);
  begin
  DoLog('Bitmex Error: ' + aMessage);
  end;

procedure TfrmWebSocketClient.BITMEXBitmexMessage(Sender: TObject;
  const aTopic: TwsBitmexTopics; const aMessage: string);
  begin
  DoLog('Bitmex Message: ' + aMessage);
  end;

procedure TfrmWebSocketClient.BITMEXBitmexSubscribed(Sender: TObject;
  const aChannel: string);
  begin
  DoLog('Bitmex Subscribed: ' + aChannel);
  end;

procedure TfrmWebSocketClient.BITMEXBitmexUnsubscribed(Sender: TObject;
  const aChannel: string);
  begin
  DoLog('Bitmex Unsubscribed: ' + aChannel);
  end;

procedure TfrmWebSocketClient.btnBitmexSubscribeClick(Sender: TObject);
  begin
  BITMEX.Subscribe(TwsBitmexTopics(cboBitmexTopics.itemIndex),
  txtBitmexSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnBitmexUnsubscribeClick(Sender: TObject);
  begin
  BITMEX.Unsubscribe(TwsBitmexTopics(cboBitmexTopics.itemIndex),
  txtBitmexSymbol.Text);
  end;

procedure TfrmWebSocketClient.btnBitmexAuthenticateClick(Sender: TObject);
  begin
  BITMEX.BITMEX.ApiKey := txtBitmexApiKey.Text;
  BITMEX.BITMEX.ApiSecret := txtBitmexApiSecret.Text;
  BITMEX.Authenticate;
  end;

procedure TfrmWebSocketClient.btnBitmexCancelAllOrdersClick(Sender: TObject);
  begin
  DoLog(BITMEX.REST_API.CancelAllOrders(txtBitmexSymbol.Text));
  end;

procedure TfrmWebSocketClient.btnBitmexGetExecutionsClick(Sender: TObject);
```

