# TidNNTPOnCheckMsgId

kind: event handler type
unit: IdNNTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdNNTPContext; const AMsgId : string; var VMsgNo : Int64) of object
```

