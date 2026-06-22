# TsgcWSOnAfterForwardHTTP

kind: event handler type
unit: sgcWebSocket_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; ARequestInfo: TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo; E: Exception) of object
```

