# TOnLocalCertificateSelectionCallback

kind: event handler type
unit: IdSSLDotNET

A handler assigned to this event must match this signature:

```pascal
procedure (ASender : TObject; AtargetHost : String; AlocalCertificates : X509CertificateCollection; AremoteCertificate : X509Certificate; AacceptableIssuers : array of String; VCert : X509Certificate) of object
```

