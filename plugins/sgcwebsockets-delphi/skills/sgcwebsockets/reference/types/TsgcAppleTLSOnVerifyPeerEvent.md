# TsgcAppleTLSOnVerifyPeerEvent

kind: event handler type
unit: sgcSSL_AppleTLS

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aCertificate: TsgcAppleTLSCertificate; aError: TsgcAppleTLSVerifyError; var Accept: Boolean) of object
```

