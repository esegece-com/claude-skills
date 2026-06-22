# TOnSetATTRIB

kind: event handler type
unit: IdFTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TIdFTPServerContext; var VAttr : UInt32; const AFileName : TIdFTPFileName; var VAUth : Boolean) of object
```

