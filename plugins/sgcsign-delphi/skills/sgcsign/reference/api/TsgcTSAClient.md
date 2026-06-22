# TsgcTSAClient

unit: sgcSign_TSA

Add `sgcSign_TSA` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `URL: string` | `string` | `__property UnicodeString URL;` |
| `HashAlgorithm: TsgcHashAlgorithm` | [TsgcHashAlgorithm](../types/TsgcHashAlgorithm.md) | `__property TsgcHashAlgorithm * HashAlgorithm;` |
| `Username: string` | `string` | `__property UnicodeString Username;` |
| `Password: string` | `string` | `__property UnicodeString Password;` |
| `Timeout: Integer` | `Integer` | `__property int Timeout;` |
| `IncludeCertificates: Boolean` | `Boolean` | `__property bool IncludeCertificates;` |
| `PolicyOID: string` | `string` | `__property UnicodeString PolicyOID;` |
| `NonceEnabled: Boolean` | `Boolean` | `__property bool NonceEnabled;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function GetTimestampToken(const aHash: TBytes; aAlgorithm: TsgcHashAlgorithm): TBytes;
function GetTimestampTokenBase64(const aHash: TBytes; aAlgorithm: TsgcHashAlgorithm): string;
```

C++Builder

```cpp
System::DynamicArray<System::Byte> __fastcall GetTimestampToken(const System::DynamicArray<System::Byte> aHash, TsgcHashAlgorithm * aAlgorithm);
UnicodeString __fastcall GetTimestampTokenBase64(const System::DynamicArray<System::Byte> aHash, TsgcHashAlgorithm * aAlgorithm);
```

