# TsgcWSErrorEvent

kind: event handler type
unit: sgcWebSocket_Protocol_WAMP2_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; MethodId: Integer; RequestId: Int64; Details, Error, Arguments, ArgumentsKw: String) of object
```

