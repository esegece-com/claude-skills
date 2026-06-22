# TIdIRCServerErrorEvent

kind: event handler type
unit: IdIRC

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TIdContext; AErrorCode: Integer; const AErrorMessage: String) of object
```

