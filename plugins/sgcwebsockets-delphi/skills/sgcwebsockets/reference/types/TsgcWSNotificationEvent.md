# TsgcWSNotificationEvent

kind: event handler type
unit: sgcWebSocket_Protocol_sgc_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; const Method, Params: string) of object
```

