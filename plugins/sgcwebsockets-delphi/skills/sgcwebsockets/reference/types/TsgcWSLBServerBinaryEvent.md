# TsgcWSLBServerBinaryEvent

kind: event handler type
unit: sgcWebSocket_LoadBalancer_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; Data: TMemoryStream; var Handled: Boolean) of object
```

