# TsgcAMQPBasicQoSEvent

kind: event handler type
unit: sgcAMQP

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aChannel: string; const aQoS: TsgcAMQPFramePayload_Method_BasicQoS) of object
```

