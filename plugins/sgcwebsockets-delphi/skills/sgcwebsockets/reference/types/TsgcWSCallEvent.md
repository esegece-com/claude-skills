# TsgcWSCallEvent

kind: event handler type
unit: sgcWebSocket_Protocol_WAMP_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; const CallId, ProcUri, Arguments: string) of object
```

