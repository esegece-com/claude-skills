# TsgcWSAPI_HTX - Example

Usage of `TsgcWSAPI_HTX` extracted from the **05.Crypto/20.HTX** demo. See the full project for context.

API reference: [TsgcWSAPI_HTX](../reference/api/TsgcWSAPI_HTX.md)
Source demo: `05.Crypto/20.HTX` (file `uHTX.pas`)

```pascal
procedure TfrmWebSocketClient.FormCreate(Sender: TObject);
  begin
  HTX.Client := WSClient;
  
  txtHost.Text := WSClient.Host;
  txtPort.Text := IntToStr(WSClient.Port);
  txtParameters.Text := WSClient.Options.Parameters;
  end;

procedure TfrmWebSocketClient.btnStartClick(Sender: TObject);
  begin
  WSClient.Host := txtHost.Text;
  WSClient.Port := StrToInt(txtPort.Text);
  WSClient.Options.Parameters := txtParameters.Text;
  WSClient.TLS := chkTLS.Checked;
  
  HTX.Huobi.ApiKey := txtHTXAPIKey.Text;
  HTX.Huobi.ApiSecret := txtHTXAPISecret.Text;
  
  WSClient.Active := True;
  if WSClient.Active then
  pnlClientOptions.Enabled := False;
  end;

FREST_API := TsgcHTTP_API_HTX.Create(nil);
procedure TfrmWebSocketClient.HTXHuobiSubscribed(Sender: TObject;
  Topic, Ts: String);
  begin
  DoLog('#HTX subscribed: ' + Topic);
  end;

procedure TfrmWebSocketClient.HTXHuobiUnSubscribed(Sender: TObject;
  Topic, Ts: String);
  begin
  DoLog('#HTX unsubscribed: ' + Topic);
  end;

procedure TfrmWebSocketClient.HTXHuobiError(Sender: TObject;
  Id, Code, Msg, Ts: string);
  begin
  DoLog('#HTX Error: ' + Code + ' - ' + Msg);
  end;

procedure TfrmWebSocketClient.btnHTXSubscribeKLineClick(Sender: TObject);
  begin
  HTX.SubscribeKLine(txtHTXSymbol.Text, hup1Min);
  end;

procedure TfrmWebSocketClient.btnHTXUnSubscribeKLineClick(Sender: TObject);
  begin
  HTX.UnSubscribeKLine(txtHTXSymbol.Text, hup1Min);
  end;

procedure TfrmWebSocketClient.btnHTXSubscribeMarketDepthClick(Sender: TObject);
  begin
  HTX.SubscribeMarketDepth(txtHTXSymbol.Text, hudStep0);
  end;

procedure TfrmWebSocketClient.btnHTXUnSubscribeMarketDepthClick(Sender: TObject);
  begin
```

