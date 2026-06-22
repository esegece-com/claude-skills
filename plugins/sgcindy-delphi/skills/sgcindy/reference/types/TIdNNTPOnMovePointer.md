# TIdNNTPOnMovePointer

kind: event handler type
unit: IdNNTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdNNTPContext; var AMsgNo: Int64; var VMsgID: string) of object
```

