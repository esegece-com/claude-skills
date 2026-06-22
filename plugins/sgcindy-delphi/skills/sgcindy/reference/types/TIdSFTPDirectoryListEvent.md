# TIdSFTPDirectoryListEvent

kind: event handler type
unit: IdSFTPClient

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aPath: string; const aItems: TIdSFTPDirectoryItems) of object
```

