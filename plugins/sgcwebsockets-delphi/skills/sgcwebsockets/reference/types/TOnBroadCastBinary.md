# TOnBroadCastBinary

kind: event handler type
unit: sgcWebSocket_LoadBalancer_Client

A handler assigned to this event must match this signature:

```pascal
procedure(aStream: TStream; const aChannel, aProtocol, aExclude, aInclude: String; aSize: Integer; aStreaming: TwsStreaming) of object
```

