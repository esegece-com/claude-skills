# TIdSFTPStatusEvent

kind: event handler type
unit: IdSFTPClient

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aStatusCode: Integer; const aMessage: string) of object
```

