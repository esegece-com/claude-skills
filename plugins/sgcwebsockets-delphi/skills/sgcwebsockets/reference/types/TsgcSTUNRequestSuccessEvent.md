# TsgcSTUNRequestSuccessEvent

kind: event handler type
unit: sgcP2P_STUN_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSocket: TsgcSocketConnection; const aRequest, aResponse: TsgcSTUN_Message; var Accept: Boolean) of object
```

