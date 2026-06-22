# TsgcAndroidTLSOnVerifyPeerEvent

kind: event handler type
unit: sgcSSL_Android_Indy

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aCertificate: TsgcAndroidTLSCertificate; aError: TsgcAndroidTLSVerifyError; var Accept: Boolean) of object
```

