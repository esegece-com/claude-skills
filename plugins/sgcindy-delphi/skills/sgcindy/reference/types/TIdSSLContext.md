# TIdSSLContext

kind: class
unit: IdSSLOpenSSL

## Properties

| Delphi | Type |
| --- | --- |
| `ALPNProtocols: TStringList` | `TStringList` |
| `CurveList: string` | `string` |
| `APIVersion: TIdSSLAPIVersion` | [TIdSSLAPIVersion](./TIdSSLAPIVersion.md) |
| `LegacyProvider: Boolean` | `Boolean` |
| `StatusInfoOn: Boolean` | `Boolean` |
| `VerifyOn: Boolean` | `Boolean` |
| `SSLVersions: TIdSSLVersions` | `TIdSSLVersions` |
| `Method: TIdSSLVersion` | [TIdSSLVersion](./TIdSSLVersion.md) |
| `Mode: TIdSSLMode` | [TIdSSLMode](./TIdSSLMode.md) |
| `RootCertFile: String` | `String` |
| `CertFile: String` | `String` |
| `CipherList: String` | `String` |
| `KeyFile: String` | `String` |
| `DHParamsFile: String` | `String` |
| `VerifyDirs: String` | `String` |
| `VerifyMode: TIdSSLVerifyModeSet` | `TIdSSLVerifyModeSet` |
| `VerifyDepth: Integer` | `Integer` |

## Methods

```pascal
function Clone: TIdSSLContext;
function LoadRootCert: Boolean;
function LoadCert: Boolean;
function LoadKey: Boolean;
function LoadDHParams: Boolean;
```

