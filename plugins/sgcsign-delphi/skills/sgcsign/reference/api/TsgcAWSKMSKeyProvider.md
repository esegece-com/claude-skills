# TsgcAWSKMSKeyProvider

unit: sgcSign_KeyProvider_AWS

Add `sgcSign_KeyProvider_AWS` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Certificate: TsgcX509Certificate (read-only)` | [TsgcX509Certificate](../types/TsgcX509Certificate.md) | `__property TsgcX509Certificate * Certificate /* read-only */;` |
| `AccessKeyId: string` | `string` | `__property UnicodeString AccessKeyId;` |
| `SecretAccessKey: string` | `string` | `__property UnicodeString SecretAccessKey;` |
| `Region: string` | `string` | `__property UnicodeString Region;` |
| `KeyId: string` | `string` | `__property UnicodeString KeyId;` |
| `ProviderType: TsgcKeyProviderType (read-only)` | [TsgcKeyProviderType](../types/TsgcKeyProviderType.md) | `__property TsgcKeyProviderType * ProviderType /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure Connect;
```

C++Builder

```cpp
void __fastcall Connect();
```

