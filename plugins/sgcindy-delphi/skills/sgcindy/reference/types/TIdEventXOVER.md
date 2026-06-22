# TIdEventXOVER

kind: event handler type
unit: IdNNTP

A handler assigned to this event must match this signature:

```pascal
procedure(AArticleIndex : Int64; ASubject, AFrom : String; ADate : TDateTime; AMsgId, AReferences : String; AByteCount, ALineCount : Integer; AExtraData : String; var VCanContinue : Boolean) of object
```

