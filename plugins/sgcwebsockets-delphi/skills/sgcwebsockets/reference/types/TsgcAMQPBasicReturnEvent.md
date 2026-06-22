# TsgcAMQPBasicReturnEvent

kind: event handler type
unit: sgcAMQP

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aChannel: string; const aReturn: TsgcAMQPFramePayload_Method_BasicReturn; const aContent: TsgcAMQPMessageContent) of object
```

