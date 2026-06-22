# TsgcWebAuthnOnMetadata

kind: event handler type
unit: sgcWebAuthn_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aAAGUID: string; var Metadata: string) of object
```

