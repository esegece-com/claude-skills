# TsgcAPIKeyOnKeyIssued

kind: event handler type
unit: sgcWebSocket_Server_APIKeyManager

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aOwner, aKey: string; const aScopes: TsgcAPIKeyScopes) of object
```

