# TsgcWSSTOMPConnectedEvent

kind: event handler type
unit: sgcWebSocket_Protocol_STOMP_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; Version, Server, Session, HeartBeat, RawHeaders: String) of object
```

