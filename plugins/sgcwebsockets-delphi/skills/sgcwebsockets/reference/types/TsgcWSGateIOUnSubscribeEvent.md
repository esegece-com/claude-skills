# TsgcWSGateIOUnSubscribeEvent

kind: event handler type
unit: sgcWebSocket_API_GateIO

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aChannel: string; aSuccess: Boolean; const aError, aRawMessage: string) of object
```

