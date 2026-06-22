# TsgcWSAPIServer_RTCMultiConnection - Example

Usage of `TsgcWSAPIServer_RTCMultiConnection` extracted from the **30.WebRTC_Protocol/04.RTCMultiConnection** demo. See the full project for context.

API reference: [TsgcWSAPIServer_RTCMultiConnection](../reference/api/TsgcWSAPIServer_RTCMultiConnection.md)
Source demo: `30.WebRTC_Protocol/04.RTCMultiConnection` (file `uServerRTCMultiConnection.pas`)

```pascal
procedure TfrmServerRTCMultiConnection.btnStartClick(Sender: TObject);
  begin
  WSServer.Port := StrToInt(txtDefaultPort.Text);
  
  // ... bindings
  With WSServer.Bindings.Add do
  begin
  Port := StrToInt(txtDefaultPort.Text);
  IP := txtHost.Text;
  end;
  
  // ... properties
  RTCMultiConnection.RTCMultiConnection.Server.Host := txtHost.Text;
  RTCMultiConnection.RTCMultiConnection.Server.Port := StrToInt(txtDefaultPort.Text);
  
  // ... active
  WSServer.Active := True;
  if WSServer.Active then
  begin
  memoLog.Lines.Add('#Server Started: ' + txtHost.Text + ':' + IntToStr(WSServer.Port));
  pnlServerOptions.Enabled := False;
  pnlBrowsers.Enabled := True;
  end;
  end;

1: result := RTCMultiConnection.RTCMultiConnection.HTMLDocuments.ScreenSharing;
2: result := RTCMultiConnection.RTCMultiConnection.HTMLDocuments.VideoBroadcasting;
3: result := RTCMultiConnection.RTCMultiConnection.HTMLDocuments.AudioConferencing;
result := RTCMultiConnection.RTCMultiConnection.HTMLDocuments.VideoConferencing;
```

