# TIdNNTPOnSelectGroup

kind: event handler type
unit: IdNNTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdNNTPContext; const AGroup: string; var VMsgCount: Int64; var VMsgFirst: Int64; var VMsgLast: Int64; var VGroupExists: Boolean) of object
```

