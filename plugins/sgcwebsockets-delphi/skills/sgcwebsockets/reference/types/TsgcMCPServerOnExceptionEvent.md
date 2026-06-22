# TsgcMCPServerOnExceptionEvent

kind: event handler type
unit: sgcWebSocket_Server_API_MCP

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; E: Exception; var aResponseCode: Integer) of object
```

