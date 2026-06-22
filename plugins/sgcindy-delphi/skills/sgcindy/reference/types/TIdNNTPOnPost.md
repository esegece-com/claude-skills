# TIdNNTPOnPost

kind: event handler type
unit: IdNNTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdNNTPContext; var VPostOk: Boolean; var VErrorText: string) of object
```

