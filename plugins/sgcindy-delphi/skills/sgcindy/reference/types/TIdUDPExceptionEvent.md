# TIdUDPExceptionEvent

kind: event handler type
unit: IdUDPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AThread: TIdUDPListenerThread; ABinding: TIdSocketHandle; const AMessage : String; const AExceptionClass : TClass) of object
```

