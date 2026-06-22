# TIdTlsServerOptions

kind: class
unit: IdTlsServerOptions

## Properties

| Delphi | Type |
| --- | --- |
| `PublicCertificate: X509Certificate` | `X509Certificate` |
| `PrivateKey: PrivateKey` | `PrivateKey` |
| `Protocol: SecurityProtocolType` | `SecurityProtocolType` |
| `ClientNeedsCertificate: Boolean` | `Boolean` |

## Methods

```pascal
procedure LoadPublicCertificateFromFile(AFileName: string);
procedure LoadPrivateKeyFromFile(AFileName: string; APassword: string = '');
```

