# TOnRetrieveFileEvent

kind: event handler type
unit: IdFTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TIdFTPServerContext; const AFileName: TIdFTPFileName; var VStream: TStream) of object
```

