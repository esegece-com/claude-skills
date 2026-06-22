# TsgcWSE2EEOnGroupMessageAckEvent

kind: event handler type
unit: sgcWebSocket_Protocol_E2EE_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aId, aFrom, aGroup, aTo, aState: string) of object
```

