# TsgcWSChallengeEvent

kind: event handler type
unit: sgcWebSocket_Protocol_WAMP2_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; AuthMethod: String; Details: string; var Secret: String) of object
```

