# TsgcSTUNResponseErrorEvent

kind: event handler type
unit: sgcP2P_STUN_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSocket: TsgcSocketConnection; const aMessage: TsgcSTUN_Message; const aError: TsgcSTUN_ResponseError) of object
```

