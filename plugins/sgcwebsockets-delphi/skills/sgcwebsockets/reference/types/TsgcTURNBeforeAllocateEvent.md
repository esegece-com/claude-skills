# TsgcTURNBeforeAllocateEvent

kind: event handler type
unit: sgcP2P_TURN_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSocket: TsgcSocketConnection; const aIP: String; aPort: Word; var Reject: Boolean) of object
```

