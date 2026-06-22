# TsgcWSOnBeforeHttp2AsyncRequest

kind: event handler type
unit: sgcWebSocket_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; Connection: TsgcWSConnection; const ARequestInfo: TIdHTTPRequestInfo; var Async: Boolean) of object
```

