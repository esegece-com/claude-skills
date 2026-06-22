# TIdEventXHDREntry

kind: event handler type
unit: IdNNTP

A handler assigned to this event must match this signature:

```pascal
procedure(AHeader : String; AMsg, AHeaderData : String; var ACanContinue: Boolean) of object
```

