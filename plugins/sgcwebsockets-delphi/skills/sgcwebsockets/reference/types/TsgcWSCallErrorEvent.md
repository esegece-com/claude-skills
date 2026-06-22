# TsgcWSCallErrorEvent

kind: event handler type
unit: sgcWebSocket_Protocol_WAMP_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; CallId, ErrorURI, ErrorDesc, ErrorDetails: string) of object
```

