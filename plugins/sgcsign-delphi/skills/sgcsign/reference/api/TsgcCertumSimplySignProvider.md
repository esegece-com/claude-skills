# TsgcCertumSimplySignProvider

unit: sgcSign_KeyProvider_Certum

Add `sgcSign_KeyProvider_Certum` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Certificate: TsgcX509Certificate (read-only)` | [TsgcX509Certificate](../types/TsgcX509Certificate.md) | `__property TsgcX509Certificate * Certificate /* read-only */;` |
| `CertificateId: string (read-only)` | `string` | `__property UnicodeString CertificateId /* read-only */;` |
| `ClientId: string` | `string` | `__property UnicodeString ClientId;` |
| `ClientSecret: string` | `string` | `__property UnicodeString ClientSecret;` |
| `Username: string` | `string` | `__property UnicodeString Username;` |
| `Password: string` | `string` | `__property UnicodeString Password;` |
| `PIN: string` | `string` | `__property UnicodeString PIN;` |
| `BaseURL: string` | `string` | `__property UnicodeString BaseURL;` |
| `ProviderType: TsgcKeyProviderType (read-only)` | [TsgcKeyProviderType](../types/TsgcKeyProviderType.md) | `__property TsgcKeyProviderType * ProviderType /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure Connect;
function ListCertificates: string;
procedure SelectCertificate(const aCertId: string);
```

C++Builder

```cpp
void __fastcall Connect();
UnicodeString __fastcall ListCertificates();
void __fastcall SelectCertificate(const UnicodeString aCertId);
```

