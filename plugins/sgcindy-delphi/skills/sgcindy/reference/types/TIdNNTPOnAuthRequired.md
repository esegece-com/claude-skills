# TIdNNTPOnAuthRequired

kind: event handler type
unit: IdNNTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdNNTPContext; const ACommand, AParams : string; var VRequired: Boolean) of object
```

