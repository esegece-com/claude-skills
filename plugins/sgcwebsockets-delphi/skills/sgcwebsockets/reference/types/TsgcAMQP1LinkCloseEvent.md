# TsgcAMQP1LinkCloseEvent

kind: event handler type
unit: sgcAMQP1

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1Link; const aDetach: TsgcAMQP1FrameDetach) of object
```

