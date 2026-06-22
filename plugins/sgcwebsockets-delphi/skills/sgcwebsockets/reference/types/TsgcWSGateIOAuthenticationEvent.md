# TsgcWSGateIOAuthenticationEvent

kind: event handler type
unit: sgcWebSocket_API_GateIO

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aSuccess: Boolean; const aError: string; const aRawMessage: string) of object
```

