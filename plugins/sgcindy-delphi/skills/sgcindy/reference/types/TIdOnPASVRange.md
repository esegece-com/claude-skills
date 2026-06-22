# TIdOnPASVRange

kind: event handler type
unit: IdFTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TIdFTPServerContext; var VIP : String; var VPortMin, VPortMax : TIdPort; const AIPVer : TIdIPVersion) of object
```

