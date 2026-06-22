# TsgcGRPCClientStreamMessageEvent

kind: event handler type
unit: sgcGRPC_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aMessage: TsgcGRPCStreamMessage; var aCancel: Boolean) of object
```

