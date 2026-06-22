# TsgcAPIKeyOnKeyRotated

kind: event handler type
unit: sgcWebSocket_Server_APIKeyManager

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aOldKey, aNewKey: string) of object
```

