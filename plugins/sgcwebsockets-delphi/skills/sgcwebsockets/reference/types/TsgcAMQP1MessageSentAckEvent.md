# TsgcAMQP1MessageSentAckEvent

kind: event handler type
unit: sgcAMQP1

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1SenderLink; const aMessageId: string; const aDeliveryState: TsgcAMQP1FrameDeliveryStates; const aDisposition: TsgcAMQP1FrameDisposition) of object
```

