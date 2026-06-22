# TsgcAMQP1BeforeReadFrameEvent

kind: event handler type
unit: sgcAMQP1

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aFrame: TsgcAMQP1Frame; var Handled: Boolean) of object
```

