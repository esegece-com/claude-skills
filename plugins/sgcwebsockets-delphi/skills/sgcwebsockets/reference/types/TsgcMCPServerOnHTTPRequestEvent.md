# TsgcMCPServerOnHTTPRequestEvent

kind: event handler type
unit: sgcWebSocket_Server_API_MCP

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aRequest: TsgcHTTPRequest; const aResponse: TsgcHTTPResponse; var Handled: Boolean) of object
```

