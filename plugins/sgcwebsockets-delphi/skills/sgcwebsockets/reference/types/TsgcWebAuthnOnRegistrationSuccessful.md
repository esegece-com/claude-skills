# TsgcWebAuthnOnRegistrationSuccessful

kind: event handler type
unit: sgcWebAuthn_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aRegistration: TsgcWebAuthn_Registration; const aCredentialRecord: TsgcWebAuthn_CredentialRecord; var Accept: Boolean) of object
```

