# TsgcAMQPChannelFlowEvent

kind: event handler type
unit: sgcAMQP

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aChannel: string; aFlow: Boolean; aAck: Boolean) of object
```

