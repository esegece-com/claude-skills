# TsgcSignatureVerifier

unit: sgcSign_Verifier

Add `sgcSign_Verifier` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `CheckCertificateValidity: Boolean` | `Boolean` | `__property bool CheckCertificateValidity;` |
| `CheckCertificateRevocation: Boolean` | `Boolean` | `__property bool CheckCertificateRevocation;` |
| `UseEmbeddedRevocationInfo: Boolean` | `Boolean` | `__property bool UseEmbeddedRevocationInfo;` |
| `OCSPClient: IsgcOCSPClient` | [IsgcOCSPClient](../types/IsgcOCSPClient.md) | `__property IsgcOCSPClient OCSPClient;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function Verify(const aSignedXML: string): TsgcVerificationStatus;
function VerifyLTV(const aSignedXML: string): TsgcVerificationStatus;
function GetVerificationDetails: string;
function GetDetailCount: Integer;
function GetDetail(aIndex: Integer): TsgcVerificationDetail;
function GetValidationReportXML: string;
```

C++Builder

```cpp
TsgcVerificationStatus * __fastcall Verify(const UnicodeString aSignedXML);
TsgcVerificationStatus * __fastcall VerifyLTV(const UnicodeString aSignedXML);
UnicodeString __fastcall GetVerificationDetails();
int __fastcall GetDetailCount();
TsgcVerificationDetail * __fastcall GetDetail(int aIndex);
UnicodeString __fastcall GetValidationReportXML();
```

