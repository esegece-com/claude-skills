# TsgcAMQPBasicDeliverEvent

kind: event handler type
unit: sgcAMQP

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aChannel: string; const aDeliver: TsgcAMQPFramePayload_Method_BasicDeliver; const aContent: TsgcAMQPMessageContent) of object
```

