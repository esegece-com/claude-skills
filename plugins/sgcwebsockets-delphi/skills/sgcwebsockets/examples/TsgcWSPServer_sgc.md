# TsgcWSPServer_sgc - Example

Usage of `TsgcWSPServer_sgc` extracted from the **01.WebSocket_Quick_Start/03.Real_Time_Monitor** demo. See the full project for context.

API reference: [TsgcWSPServer_sgc](../reference/api/TsgcWSPServer_sgc.md)
Source demo: `01.WebSocket_Quick_Start/03.Real_Time_Monitor` (file `fServer.pas`)

```pascal
procedure TfrmServer.Timer1Timer(Sender: TObject);
  var
  i: Integer;
  begin
  if WSServer.Count > 0 then
  begin
  i := RandomRange(1, 5);
  case i of
  1: WSServer_sgc.Publish(IntToStr(cpu), 'cpu');
  2: WSServer_sgc.Publish(IntToStr(memory), 'memory');
  3: WSServer_sgc.Publish(IntToStr(network), 'network');
  end;
  end;

```

