# TsgcTURNMessageDiscardedEvent

kind: event handler type
unit: sgcP2P_TURN_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSocket: TsgcSocketConnection; aMethod: TsgcStunMessageMethod; const aMessage: TsgcSTUN_Message; const aReason: string) of object
```

