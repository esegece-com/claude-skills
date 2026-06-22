# TsgcPEMKeyProvider

unit: sgcSign_KeyProvider_PEM

Add `sgcSign_KeyProvider_PEM` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Certificate: TsgcX509Certificate (read-only)` | [TsgcX509Certificate](../types/TsgcX509Certificate.md) | `__property TsgcX509Certificate * Certificate /* read-only */;` |
| `CertificateLoaded: Boolean (read-only)` | `Boolean` | `__property bool CertificateLoaded /* read-only */;` |
| `HashAlgorithm: TsgcHashAlgorithm` | [TsgcHashAlgorithm](../types/TsgcHashAlgorithm.md) | `__property TsgcHashAlgorithm * HashAlgorithm;` |
| `CertificateFile: string` | `string` | `__property UnicodeString CertificateFile;` |
| `PrivateKeyFile: string` | `string` | `__property UnicodeString PrivateKeyFile;` |
| `PrivateKeyPassword: string` | `string` | `__property UnicodeString PrivateKeyPassword;` |
| `ProviderType: TsgcKeyProviderType (read-only)` | [TsgcKeyProviderType](../types/TsgcKeyProviderType.md) | `__property TsgcKeyProviderType * ProviderType /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure LoadFromFile;
procedure LoadCertificateOnly;
function SignDataPSS(const aData: TBytes): TBytes;
```

C++Builder

```cpp
void __fastcall LoadFromFile();
void __fastcall LoadCertificateOnly();
System::DynamicArray<System::Byte> __fastcall SignDataPSS(const System::DynamicArray<System::Byte> aData);
```

