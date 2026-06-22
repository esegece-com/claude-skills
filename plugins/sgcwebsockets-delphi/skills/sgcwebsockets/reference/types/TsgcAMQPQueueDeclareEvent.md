# TsgcAMQPQueueDeclareEvent

kind: event handler type
unit: sgcAMQP

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aChannel, aQueue: string; aMessageCount, aConsumerCount: Integer) of object
```

