# TOnListDirectoryEvent

kind: event handler type
unit: IdFTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TIdFTPServerContext; const APath: TIdFTPFileName; ADirectoryListing: TIdFTPListOutput; const ACmd : String; const ASwitches : String) of object
```

