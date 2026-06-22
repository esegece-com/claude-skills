# TsgcGCloudKMSKeyProvider

unit: sgcSign_KeyProvider_GCloud

Add `sgcSign_KeyProvider_GCloud` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Certificate: TsgcX509Certificate (read-only)` | [TsgcX509Certificate](../types/TsgcX509Certificate.md) | `__property TsgcX509Certificate * Certificate /* read-only */;` |
| `ProjectId: string` | `string` | `__property UnicodeString ProjectId;` |
| `LocationId: string` | `string` | `__property UnicodeString LocationId;` |
| `KeyRingId: string` | `string` | `__property UnicodeString KeyRingId;` |
| `KeyId: string` | `string` | `__property UnicodeString KeyId;` |
| `KeyVersion: string` | `string` | `__property UnicodeString KeyVersion;` |
| `ServiceAccountJSON: string` | `string` | `__property UnicodeString ServiceAccountJSON;` |
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

