# TsgcSTUNRequestAuthorizationEvent

kind: event handler type
unit: sgcP2P_STUN_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aRequest: TsgcSTUN_Message; const aUsername, aRealm: string; var Password: string) of object
```

