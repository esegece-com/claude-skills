# TIdFingerGetEvent

kind: event handler type
unit: IdFingerServer

A handler assigned to this event must match this signature:

```pascal
procedure (AContext:TIdContext; const AUserName: String; var VResponse : String) of object
```

