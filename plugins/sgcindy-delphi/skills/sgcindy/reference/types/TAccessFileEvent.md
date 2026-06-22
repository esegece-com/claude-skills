# TAccessFileEvent

kind: event handler type
unit: IdTrivialFTPServer

A handler assigned to this event must match this signature:

```pascal
procedure (Sender: TObject; var FileName: String; const PeerInfo: TPeerInfo; var GrantAccess: Boolean; var AStream: TStream; var FreeStreamOnComplete: Boolean) of object
```

