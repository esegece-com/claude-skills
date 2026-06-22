# TsgcAMQP1SessionOpenEvent

kind: event handler type
unit: sgcAMQP1_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSession: TsgcAMQP1Session; const aBegin: TsgcAMQP1FrameBegin) of object
```

