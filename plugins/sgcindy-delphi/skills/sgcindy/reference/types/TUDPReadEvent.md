# TUDPReadEvent

kind: event handler type
unit: IdUDPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AThread: TIdUDPListenerThread; const AData: TIdBytes; ABinding: TIdSocketHandle) of object
```

