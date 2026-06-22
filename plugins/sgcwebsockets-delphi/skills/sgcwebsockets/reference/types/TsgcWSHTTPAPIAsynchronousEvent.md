# TsgcWSHTTPAPIAsynchronousEvent

kind: event handler type
unit: sgcWebSocket_HTTPAPI_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; var aConnection: TsgcHTTPAPIContext; var Handled: Boolean) of object
```

