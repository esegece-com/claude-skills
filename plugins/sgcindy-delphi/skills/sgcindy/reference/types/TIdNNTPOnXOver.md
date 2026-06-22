# TIdNNTPOnXOver

kind: event handler type
unit: IdNNTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdNNTPContext; const AMsgFirst: Int64; const AMsgLast: Int64) of object
```

