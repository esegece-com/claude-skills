# TPasswordEventEx

kind: event handler type
unit: IdSSLOpenSSL

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TObject; var VPassword: String; const AIsWrite: Boolean) of object
```

