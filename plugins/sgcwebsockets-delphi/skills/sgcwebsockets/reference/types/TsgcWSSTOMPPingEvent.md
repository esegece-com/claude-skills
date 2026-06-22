# TsgcWSSTOMPPingEvent

kind: event handler type
unit: sgcWebSocket_Protocol_STOMP_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; aPing: TsgcSTOMPPingMode; aLastIncoming: TDateTime; aLastOutgoing: TDateTime) of object
```

