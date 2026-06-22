# TsgcWebAuthnOnHTTPRequest

kind: event handler type
unit: sgcWebSocket_Server_API_WebAuthn

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aMethod: TsgcWebAuthnHTTPRequestMethod; const aRequest: TsgcHTTPRequest; var Accept: Boolean) of object
```

