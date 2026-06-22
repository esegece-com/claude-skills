# TsgcGRPCClientBeforeRequestEvent

kind: event handler type
unit: sgcGRPC_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aService, aMethod: string; var aMetadata: TsgcGRPCMetadata) of object
```

