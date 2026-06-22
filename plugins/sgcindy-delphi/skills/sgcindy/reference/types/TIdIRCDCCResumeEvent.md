# TIdIRCDCCResumeEvent

kind: event handler type
unit: IdIRC

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TIdContext; const ANickname, AHost, AFilename: String; APort: TIdPort; AFilePos: Int64) of object
```

