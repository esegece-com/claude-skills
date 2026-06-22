# TIdSFTPErrorEvent

kind: event handler type
unit: IdSFTPClient

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aErrorCode: Integer; const aErrorMessage: string) of object
```

