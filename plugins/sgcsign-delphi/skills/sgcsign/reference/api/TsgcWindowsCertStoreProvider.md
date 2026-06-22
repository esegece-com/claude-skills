# TsgcWindowsCertStoreProvider

unit: sgcSign_KeyProvider_WinCertStore

Add `sgcSign_KeyProvider_WinCertStore` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Certificate: TsgcX509Certificate (read-only)` | [TsgcX509Certificate](../types/TsgcX509Certificate.md) | `__property TsgcX509Certificate * Certificate /* read-only */;` |
| `IsLoaded: Boolean (read-only)` | `Boolean` | `__property bool IsLoaded /* read-only */;` |
| `HashAlgorithm: TsgcHashAlgorithm` | [TsgcHashAlgorithm](../types/TsgcHashAlgorithm.md) | `__property TsgcHashAlgorithm * HashAlgorithm;` |
| `StoreName: string` | `string` | `__property UnicodeString StoreName;` |
| `StoreLocation: TsgcCertStoreLocation` | [TsgcCertStoreLocation](../types/TsgcCertStoreLocation.md) | `__property TsgcCertStoreLocation * StoreLocation;` |
| `ProviderType: TsgcKeyProviderType (read-only)` | [TsgcKeyProviderType](../types/TsgcKeyProviderType.md) | `__property TsgcKeyProviderType * ProviderType /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure SelectCertificateBySubject(const aSubjectFilter: string);
procedure SelectCertificateByThumbprint(const aThumbprint: string);
function EnumerateCertificates: TStringList;
```

C++Builder

```cpp
void __fastcall SelectCertificateBySubject(const UnicodeString aSubjectFilter);
void __fastcall SelectCertificateByThumbprint(const UnicodeString aThumbprint);
TStringList * __fastcall EnumerateCertificates();
```

