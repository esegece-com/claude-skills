# TIdSFTPProgressEvent

kind: event handler type
unit: IdSFTPClient

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aFileName: string; aTransferred, aTotal: Int64; var aCancel: Boolean) of object
```

