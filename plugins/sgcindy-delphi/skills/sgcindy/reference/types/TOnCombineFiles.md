# TOnCombineFiles

kind: event handler type
unit: IdFTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TIdFTPServerContext; const ATargetFileName: TIdFTPFileName; AParts : TStrings) of object
```

