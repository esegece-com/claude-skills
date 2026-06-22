# TsgcWebAuthnOnRegistrationError

kind: event handler type
unit: sgcWebAuthn_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aRequest: TsgcWebAuthn_RegistrationVerify_Request; const aRegistration: TsgcWebAuthn_Registration; const aError: string) of object
```

