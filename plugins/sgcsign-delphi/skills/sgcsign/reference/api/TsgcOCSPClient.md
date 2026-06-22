# TsgcOCSPClient

unit: sgcSign_OCSP

Add `sgcSign_OCSP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Timeout: Integer` | `Integer` | `__property int Timeout;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function CheckCertificateAuto(const aCertData, aIssuerData: TBytes) : TsgcVerificationStatus;
function CheckCertificateURL(const aCertData, aIssuerData: TBytes; const aOCSPURL: string): TsgcVerificationStatus;
function GetRawOCSPResponse(const aCertData, aIssuerData: TBytes; const aOCSPURL: string): TBytes;
```

C++Builder

```cpp
TsgcVerificationStatus * __fastcall CheckCertificateAuto(const System::DynamicArray<System::Byte> aCertData, const System::DynamicArray<System::Byte> aIssuerData);
TsgcVerificationStatus * __fastcall CheckCertificateURL(const System::DynamicArray<System::Byte> aCertData, const System::DynamicArray<System::Byte> aIssuerData, const UnicodeString aOCSPURL);
System::DynamicArray<System::Byte> __fastcall GetRawOCSPResponse(const System::DynamicArray<System::Byte> aCertData, const System::DynamicArray<System::Byte> aIssuerData, const UnicodeString aOCSPURL);
```

