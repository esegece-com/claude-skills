# TWorkEvent

kind: event handler type
unit: IdComponent

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TObject; AWorkMode: TWorkMode; AWorkCount: Int64) of object
```

