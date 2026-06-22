# TsgcAMQPBasicGetOkEvent

kind: event handler type
unit: sgcAMQP

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aChannel: string; const aGetOk: TsgcAMQPFramePayload_Method_BasicGetOk; const aContent: TsgcAMQPMessageContent) of object
```

