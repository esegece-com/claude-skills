# TsgcAMQPDisconnectEvent

kind: event handler type
unit: sgcAMQP

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aClose: TsgcAMQPFramePayload_Method_ConnectionClose; aAck: Boolean) of object
```

