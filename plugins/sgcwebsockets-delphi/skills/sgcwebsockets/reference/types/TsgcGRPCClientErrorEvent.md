# TsgcGRPCClientErrorEvent

kind: event handler type
unit: sgcGRPC_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aStatusCode: TsgcGRPCStatusCode; const aStatusMessage: string) of object
```

