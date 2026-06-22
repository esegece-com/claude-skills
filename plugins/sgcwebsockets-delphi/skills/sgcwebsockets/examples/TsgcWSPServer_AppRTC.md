# TsgcWSPServer_AppRTC - Example

Usage of `TsgcWSPServer_AppRTC` extracted from the **30.WebRTC_Protocol/01.AppRTC** demo. See the full project for context.

API reference: [TsgcWSPServer_AppRTC](../reference/api/TsgcWSPServer_AppRTC.md)
Source demo: `30.WebRTC_Protocol/01.AppRTC` (file `uServerAppRTC.pas`)

```pascal
procedure TfrmServerWebRTC.btnStartClick(Sender: TObject);
  begin
  WSServer.Port := StrToInt(txtDefaultPort.Text);
  
  // ... bindings
  With WSServer.Bindings.Add do
  begin
  Port := StrToInt(txtDefaultPort.Text);
  IP := txtHost.Text;
  end;
  
  // ... properties
  WSPAppRTC.AppRTC.RoomLink := 'https://' + txtHost.Text + ':' + txtDefaultPort.Text + '/r/';
  WSPAppRTC.AppRTC.WebSocketURL := 'wss://' + txtHost.Text + ':' + txtDefaultPort.Text;
  
  // ... active
  WSServer.Active := True;
  if WSServer.Active then
  begin
  memoLog.Lines.Add('#Server Started: ' + txtHost.Text + ':' + IntToStr(WSServer.Port));
  pnlServerOptions.Enabled := False;
  pnlBrowsers.Enabled := True;
  end;
  end;

```

