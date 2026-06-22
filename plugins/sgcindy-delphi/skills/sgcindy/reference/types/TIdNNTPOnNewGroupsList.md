# TIdNNTPOnNewGroupsList

kind: event handler type
unit: IdNNTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdNNTPContext; const ADateStamp : TDateTime; const ADistributions : String) of object
```

