# TsgcWSPClient_Files - Example

Usage of `TsgcWSPClient_Files` extracted from the **02.WebSocket_Protocols/02.Send_Receive_Files_Protocol** demo. See the full project for context.

API reference: [TsgcWSPClient_Files](../reference/api/TsgcWSPClient_Files.md)
Source demo: `02.WebSocket_Protocols/02.Send_Receive_Files_Protocol` (file `fClientFiles.pas`)

```pascal
procedure TFRMClientFiles.btnSubscribeClick(Sender: TObject);
  begin
  client_files.Subscribe('test');
  end;

client_files.Files.BufferSize := TrackSize.Position;
client_files.Files.QoS.Level := TwsQoS(Ord(cboQoS.ItemIndex));
client_files.Files.SaveDirectory := txtSaveDirectory.Text;
```

