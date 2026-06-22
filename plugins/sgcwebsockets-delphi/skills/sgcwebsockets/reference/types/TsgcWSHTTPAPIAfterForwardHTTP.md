# TsgcWSHTTPAPIAfterForwardHTTP

kind: event handler type
unit: sgcWebSocket_Server_HTTPAPI

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; aRequestInfo: THttpServerRequest; var aResponseInfo: THttpServerResponse; E: Exception) of object
```

