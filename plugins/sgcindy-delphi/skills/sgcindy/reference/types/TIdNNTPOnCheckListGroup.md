# TIdNNTPOnCheckListGroup

kind: event handler type
unit: IdNNTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdNNTPContext; const AGroup: string; var VCanJoin : Boolean; var VFirstArticle : Int64) of object
```

