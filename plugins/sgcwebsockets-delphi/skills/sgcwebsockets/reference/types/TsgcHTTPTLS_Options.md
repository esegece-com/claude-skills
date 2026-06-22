# TsgcHTTPTLS_Options

kind: class
unit: sgcHTTP_Client

## Properties

| Delphi | Type |
| --- | --- |
| `ALPNProtocols: TStringList` | `TStringList` |
| `IOHandler: TwsTLSIOHandler` | [TwsTLSIOHandler](./TwsTLSIOHandler.md) |
| `OpenSSL_Options: TsgcOpenSSLClient_Options` | [TsgcOpenSSLClient_Options](./TsgcOpenSSLClient_Options.md) |
| `SChannel_Options: TsgcSChannelClient_Options` | [TsgcSChannelClient_Options](./TsgcSChannelClient_Options.md) |
| `CertFile: String` | `String` |
| `KeyFile: String` | `String` |
| `Password:  (read-only)` |  |
| `RootCertFile: String` | `String` |
| `VerifyCertificate: Boolean` | `Boolean` |
| `VerifyDepth: Integer` | `Integer` |
| `Version: TwsTLSVersions` | [TwsTLSVersions](./TwsTLSVersions.md) |

## Methods

```pascal
procedure Assign(aSource: TPersistent);
```

