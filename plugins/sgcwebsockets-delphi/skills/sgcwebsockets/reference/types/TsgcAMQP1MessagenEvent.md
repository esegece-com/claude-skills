# TsgcAMQP1MessagenEvent

kind: event handler type
unit: sgcAMQP1

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1ReceiverLink; const aMessage: TsgcAMQP1Message; var DeliveryState: TsgcAMQP1MessageDeliveryState) of object
```

