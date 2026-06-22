# TsgcWSPServer_WebRTC - Example

Usage of `TsgcWSPServer_WebRTC` extracted from the **30.WebRTC_Protocol/03.WebRTC** demo. See the full project for context.

API reference: [TsgcWSPServer_WebRTC](../reference/api/TsgcWSPServer_WebRTC.md)
Source demo: `30.WebRTC_Protocol/03.WebRTC` (file `uServerWebRTC.pas`)

```pascal
procedure TfrmServerWebRTC.WSPWebRTCMessage(Connection: TsgcWSConnection; const
  Text: string);
  begin
  memoLog.Lines.Add('Message: ' + Connection.IP + ' - ' + Text);
  WSPWebRTC.Broadcast(Text, txtChannel.Text);
  end;

```

