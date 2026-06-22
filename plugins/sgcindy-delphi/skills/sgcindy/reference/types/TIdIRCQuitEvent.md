# TIdIRCQuitEvent

kind: event handler type
unit: IdIRC

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TIdContext; const ANickname, AHost, AReason: String) of object
```

