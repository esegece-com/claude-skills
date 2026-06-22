# TsgcAMQP1LinkOpenEvent

kind: event handler type
unit: sgcAMQP1

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1Link; const aAttach: TsgcAMQP1FrameAttach) of object
```

