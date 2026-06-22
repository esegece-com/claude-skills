# TsgcAMQPChannelCloseEvent

kind: event handler type
unit: sgcAMQP

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aChannel: string; const aChannelClose: TsgcAMQPFramePayload_Method_ChannelClose; aAck: Boolean) of object
```

