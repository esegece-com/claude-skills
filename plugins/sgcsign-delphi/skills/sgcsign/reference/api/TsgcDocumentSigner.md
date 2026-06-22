# TsgcDocumentSigner

unit: sgcSign_DocumentSigner

Add `sgcSign_DocumentSigner` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `KeyProvider: IsgcKeyProvider` | [IsgcKeyProvider](../types/IsgcKeyProvider.md) | `__property IsgcKeyProvider KeyProvider;` |
| `Profile: TsgcSignatureProfile` | [TsgcSignatureProfile](../types/TsgcSignatureProfile.md) | `__property TsgcSignatureProfile * Profile;` |
| `Format: TsgcSignatureFormat` | [TsgcSignatureFormat](../types/TsgcSignatureFormat.md) | `__property TsgcSignatureFormat * Format;` |
| `TSAClient: IsgcTSAClient` | [IsgcTSAClient](../types/IsgcTSAClient.md) | `__property IsgcTSAClient TSAClient;` |
| `XAdESType: TsgcXAdESType` | [TsgcXAdESType](../types/TsgcXAdESType.md) | `__property TsgcXAdESType * XAdESType;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function SignXML(const aSourceXML: string): string;
function SignXMLDetached(const aSourceXML: string; const aReferenceURI: string): string;
function SignXMLEnveloping(const aSourceXML: string): string;
```

C++Builder

```cpp
UnicodeString __fastcall SignXML(const UnicodeString aSourceXML);
UnicodeString __fastcall SignXMLDetached(const UnicodeString aSourceXML, const UnicodeString aReferenceURI);
UnicodeString __fastcall SignXMLEnveloping(const UnicodeString aSourceXML);
```

