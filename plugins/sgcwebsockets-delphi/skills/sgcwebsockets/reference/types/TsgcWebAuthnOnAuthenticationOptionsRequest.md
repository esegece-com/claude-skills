# TsgcWebAuthnOnAuthenticationOptionsRequest

kind: event handler type
unit: sgcWebAuthn_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aRequest: TsgcWebAuthn_AuthenticationOptions_Request; var CredentialRecords: TsgcWebAuthn_CredentialRecords; var Accept: Boolean) of object
```

