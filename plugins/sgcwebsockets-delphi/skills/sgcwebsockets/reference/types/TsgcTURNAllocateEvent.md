# TsgcTURNAllocateEvent

kind: event handler type
unit: sgcP2P_TURN_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message; const aAllocation: TsgcTURN_ResponseAllocation) of object
```

