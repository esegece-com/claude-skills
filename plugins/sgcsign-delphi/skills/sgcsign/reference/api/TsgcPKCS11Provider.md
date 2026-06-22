# TsgcPKCS11Provider

unit: sgcSign_KeyProvider_PKCS11

Add `sgcSign_KeyProvider_PKCS11` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Certificate: TsgcX509Certificate (read-only)` | [TsgcX509Certificate](../types/TsgcX509Certificate.md) | `__property TsgcX509Certificate * Certificate /* read-only */;` |
| `IsInitialized: Boolean (read-only)` | `Boolean` | `__property bool IsInitialized /* read-only */;` |
| `IsLoggedIn: Boolean (read-only)` | `Boolean` | `__property bool IsLoggedIn /* read-only */;` |
| `LibraryPath: string` | `string` | `__property UnicodeString LibraryPath;` |
| `SlotIndex: Integer` | `Integer` | `__property int SlotIndex;` |
| `PIN: string` | `string` | `__property UnicodeString PIN;` |
| `CertificateLabel: string` | `string` | `__property UnicodeString CertificateLabel;` |
| `ProviderType: TsgcKeyProviderType (read-only)` | [TsgcKeyProviderType](../types/TsgcKeyProviderType.md) | `__property TsgcKeyProviderType * ProviderType /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnProgress: TsgcPKCS11ProgressEvent` | [TsgcPKCS11ProgressEvent](../types/TsgcPKCS11ProgressEvent.md) | `__property TsgcPKCS11ProgressEvent OnProgress;` |

## Methods

Delphi

```pascal
procedure Connect;
procedure Disconnect;
function EnumerateSlots: TStringList;
function EnumerateCertificates: TStringList;
```

C++Builder

```cpp
void __fastcall Connect();
void __fastcall Disconnect();
TStringList * __fastcall EnumerateSlots();
TStringList * __fastcall EnumerateCertificates();
```

