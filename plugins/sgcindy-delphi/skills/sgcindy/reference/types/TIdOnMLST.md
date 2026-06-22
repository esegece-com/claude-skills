# TIdOnMLST

kind: event handler type
unit: IdFTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(ASender : TIdFTPServerContext; const APath: TIdFTPFileName; ADirectoryListing: TIdFTPListOutput) of object
```

