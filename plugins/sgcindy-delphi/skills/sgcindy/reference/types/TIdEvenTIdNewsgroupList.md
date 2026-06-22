# TIdEvenTIdNewsgroupList

kind: event handler type
unit: IdNNTP

A handler assigned to this event must match this signature:

```pascal
procedure(ANewsgroup: string; ALow, AHigh: Int64; AType: string; var ACanContinue: Boolean) of object
```

