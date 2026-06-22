# TsgcWebAuthnOnHTTPResponse

kind: event handler type
unit: sgcWebSocket_Server_API_WebAuthn

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aMethod: TsgcWebAuthnHTTPRequestMethod; const aRequest: TsgcHTTPRequest; const aResponse: TsgcHTTPResponse) of object
```

