# TsgcWebAuthnOnAuthenticationError

kind: event handler type
unit: sgcWebAuthn_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aRequest: TsgcWebAuthn_AuthenticationVerify_Request; const aError: string) of object
```

