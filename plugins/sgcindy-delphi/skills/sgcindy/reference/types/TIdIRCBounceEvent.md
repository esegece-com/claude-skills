# TIdIRCBounceEvent

kind: event handler type
unit: IdIRC

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TIdContext; const AHost: String; APort: Integer; const AInfo: String) of object
```

