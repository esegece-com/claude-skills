# TOnValidatePeerCertificate

kind: event handler type
unit: IdSSLDotNET

A handler assigned to this event must match this signature:

```pascal
procedure (ASender : TObject; ACertificate : X509Certificate; AChain : X509Chain; AsslPolicyErrors : SslPolicyErrors; var VValid : Boolean) of object
```

