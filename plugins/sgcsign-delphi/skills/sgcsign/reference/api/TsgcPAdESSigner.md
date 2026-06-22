# TsgcPAdESSigner

unit: sgcSign_PAdES

Add `sgcSign_PAdES` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `KeyProvider: IsgcKeyProvider` | [IsgcKeyProvider](../types/IsgcKeyProvider.md) | `__property IsgcKeyProvider KeyProvider;` |
| `Profile: TsgcSignProfileConfig` | [TsgcSignProfileConfig](../types/TsgcSignProfileConfig.md) | `__property TsgcSignProfileConfig * Profile;` |
| `TSAClient: IsgcTSAClient` | [IsgcTSAClient](../types/IsgcTSAClient.md) | `__property IsgcTSAClient TSAClient;` |
| `Reason: string` | `string` | `__property UnicodeString Reason;` |
| `Location: string` | `string` | `__property UnicodeString Location;` |
| `ContactInfo: string` | `string` | `__property UnicodeString ContactInfo;` |
| `SignerName: string` | `string` | `__property UnicodeString SignerName;` |
| `SignatureFieldName: string` | `string` | `__property UnicodeString SignatureFieldName;` |
| `VisibleSignature: TsgcPAdESVisibleSignature` | [TsgcPAdESVisibleSignature](../types/TsgcPAdESVisibleSignature.md) | `__property TsgcPAdESVisibleSignature * VisibleSignature;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure SignPDF(aInput: TStream; aOutput: TStream);
procedure SignPDFFile(const aInputFile, aOutputFile: string);
function SignPDFBytes(const aInputPDF: TBytes): TBytes;
```

C++Builder

```cpp
void __fastcall SignPDF(TStream * aInput, TStream * aOutput);
void __fastcall SignPDFFile(const UnicodeString aInputFile, const UnicodeString aOutputFile);
System::DynamicArray<System::Byte> __fastcall SignPDFBytes(const System::DynamicArray<System::Byte> aInputPDF);
```

