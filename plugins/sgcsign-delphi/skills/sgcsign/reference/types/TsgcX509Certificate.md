# TsgcX509Certificate

kind: class
unit: sgcSign_X509

## Properties

| Delphi | Type |
| --- | --- |
| `RawData: TBytes (read-only)` | `TBytes` |
| `Version: Integer (read-only)` | `Integer` |
| `SerialNumber: string (read-only)` | `string` |
| `Issuer: string (read-only)` | `string` |
| `Subject: string` | `string` |
| `NotBefore: TDateTime (read-only)` | `TDateTime` |
| `NotAfter: TDateTime (read-only)` | `TDateTime` |
| `NotBeforeLocal: TDateTime (read-only)` | `TDateTime` |
| `NotAfterLocal: TDateTime (read-only)` | `TDateTime` |
| `PublicKeyAlgorithm: string (read-only)` | `string` |
| `PublicKeyData: TBytes (read-only)` | `TBytes` |
| `PublicKeyParameters: TBytes (read-only)` | `TBytes` |
| `SignatureAlgorithm: string (read-only)` | `string` |
| `SubjectCN: string (read-only)` | `string` |
| `SubjectO: string (read-only)` | `string` |
| `SubjectOU: string (read-only)` | `string` |
| `SubjectC: string (read-only)` | `string` |
| `SubjectSerialNumber: string (read-only)` | `string` |
| `IssuerCN: string (read-only)` | `string` |
| `IssuerO: string (read-only)` | `string` |
| `IsCA: Boolean (read-only)` | `Boolean` |
| `KeyUsage: Cardinal (read-only)` | `Cardinal` |
| `ThumbprintSHA1: string (read-only)` | `string` |
| `ThumbprintSHA256: string (read-only)` | `string` |
| `CertificateData: TBytes` | `TBytes` |

## Methods

```pascal
procedure LoadFromDER(const aData: TBytes);
procedure LoadFromPEM(const aPEM: string);
procedure LoadFromFile(const aFileName: string);
function ToDER: TBytes;
function ToPEM: string;
function GetDigest(aAlgorithm: TsgcHashAlgorithm): TBytes;
function GetIssuerSerial: string;
function IsExpired: Boolean;
function IsValidAt(aDate: TDateTime): Boolean;
function IsSelfSigned: Boolean;
function GetSubjectAltNameCount: Integer;
function GetSubjectAltName(aIndex: Integer): string;
function GetAIAURLCount: Integer;
function GetAIAURL(aIndex: Integer): string;
function GetCDPURLCount: Integer;
function GetCDPURL(aIndex: Integer): string;
function GetExtKeyUsageCount: Integer;
function GetExtKeyUsageOID(aIndex: Integer): string;
function HasKeyUsageDigitalSignature: Boolean;
function HasKeyUsageNonRepudiation: Boolean;
function GetBase64Encoded: string;
```

