# TIdLPRStatusEvent

kind: event handler type
unit: IdLPR

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TObject; const AStatus: TIdLPRStatus; const AStatusText: String) of object
```

