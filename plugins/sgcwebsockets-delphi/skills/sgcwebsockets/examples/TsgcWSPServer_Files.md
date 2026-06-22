# TsgcWSPServer_Files - Example

Usage of `TsgcWSPServer_Files` extracted from the **02.WebSocket_Protocols/02.Send_Receive_Files_Protocol** demo. See the full project for context.

API reference: [TsgcWSPServer_Files](../reference/api/TsgcWSPServer_Files.md)
Source demo: `02.WebSocket_Protocols/02.Send_Receive_Files_Protocol` (file `fServerFiles.pas`)

```pascal
server_files.Files.BufferSize := TrackSize.Position;
server_files.Files.QoS.Level := TwsQoS(Ord(cboQoS.ItemIndex));
server_files.Files.SaveDirectory := txtSaveDirectory.Text;
```

