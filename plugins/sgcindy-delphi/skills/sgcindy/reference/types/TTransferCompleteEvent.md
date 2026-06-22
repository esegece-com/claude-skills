# TTransferCompleteEvent

kind: event handler type
unit: IdTrivialFTPServer

A handler assigned to this event must match this signature:

```pascal
procedure (Sender: TObject; const Success: Boolean; const PeerInfo: TPeerInfo; var AStream: TStream; const WriteOperation: Boolean) of object
```

