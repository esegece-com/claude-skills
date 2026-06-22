# TsgcPFXKeyProvider

unit: sgcSign_KeyProvider_PFX

Add `sgcSign_KeyProvider_PFX` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Certificate: TsgcX509Certificate (read-only)` | [TsgcX509Certificate](../types/TsgcX509Certificate.md) | `__property TsgcX509Certificate * Certificate /* read-only */;` |
| `FileName: string` | `string` | `__property UnicodeString FileName;` |
| `Password: string` | `string` | `__property UnicodeString Password;` |
| `HashAlgorithm: TsgcHashAlgorithm` | [TsgcHashAlgorithm](../types/TsgcHashAlgorithm.md) | `__property TsgcHashAlgorithm * HashAlgorithm;` |
| `ProviderType: TsgcKeyProviderType (read-only)` | [TsgcKeyProviderType](../types/TsgcKeyProviderType.md) | `__property TsgcKeyProviderType * ProviderType /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure LoadFromFile;
procedure LoadFromBytes(const aPFXData: TBytes; const aPassword: string);
```

C++Builder

```cpp
void __fastcall LoadFromFile();
void __fastcall LoadFromBytes(const System::DynamicArray<System::Byte> aPFXData, const UnicodeString aPassword);
```

