# TsgcHashiCorpVaultKeyProvider

unit: sgcSign_KeyProvider_Vault

Add `sgcSign_KeyProvider_Vault` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `ExternalCertificate: TsgcX509Certificate (read-only)` | [TsgcX509Certificate](../types/TsgcX509Certificate.md) | `__property TsgcX509Certificate * ExternalCertificate /* read-only */;` |
| `VaultAddress: string` | `string` | `__property UnicodeString VaultAddress;` |
| `Token: string` | `string` | `__property UnicodeString Token;` |
| `MountPath: string` | `string` | `__property UnicodeString MountPath;` |
| `KeyName: string` | `string` | `__property UnicodeString KeyName;` |
| `ProviderType: TsgcKeyProviderType (read-only)` | [TsgcKeyProviderType](../types/TsgcKeyProviderType.md) | `__property TsgcKeyProviderType * ProviderType /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure Connect;
procedure SetCertificate(const aCertDER: TBytes);
procedure SetCertificateFromFile(const aFileName: string);
```

C++Builder

```cpp
void __fastcall Connect();
void __fastcall SetCertificate(const System::DynamicArray<System::Byte> aCertDER);
void __fastcall SetCertificateFromFile(const UnicodeString aFileName);
```

