# TsgcWebSocketProxyServer - Example

Usage of `TsgcWebSocketProxyServer` extracted from the **04.WebSocket_Other_Samples/05.Proxy_Server** demo. See the full project for context.

API reference: [TsgcWebSocketProxyServer](../reference/api/TsgcWebSocketProxyServer.md)
Source demo: `04.WebSocket_Other_Samples/05.Proxy_Server` (file `fServerProxy.pas`)

```pascal
procedure TfrmServerProxy.btnStartClick(Sender: TObject);
  begin
  if not WSServer.Active then
  begin
  WSServer.Active := True;
  btnStart.Enabled := False;
  btnStop.Enabled := True;
  end;
  end;

procedure TfrmServerProxy.btnStopClick(Sender: TObject);
  begin
  if WSServer.Active then
  begin
  WSServer.Active := False;
  btnStart.Enabled := True;
  btnStop.Enabled := False;
  end;
  end;

```

