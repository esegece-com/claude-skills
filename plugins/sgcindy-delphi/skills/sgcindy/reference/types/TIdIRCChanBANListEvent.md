# TIdIRCChanBANListEvent

kind: event handler type
unit: IdIRC

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TIdContext; const AChannel: String; ABanList: TStrings) of object
```

