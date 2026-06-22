# TsgcXAdESSigner

unit: sgcSign_XAdES

Add `sgcSign_XAdES` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Certificate: sgcSign_X509.TsgcX509Certificate (read-only)` | [TsgcX509Certificate](../types/TsgcX509Certificate.md) | `__property sgcSign_X509.TsgcX509Certificate Certificate /* read-only */;` |
| `KeyProvider: IsgcKeyProvider` | [IsgcKeyProvider](../types/IsgcKeyProvider.md) | `__property IsgcKeyProvider KeyProvider;` |
| `Profile: TsgcSignProfileConfig` | [TsgcSignProfileConfig](../types/TsgcSignProfileConfig.md) | `__property TsgcSignProfileConfig * Profile;` |
| `XAdESType: TsgcXAdESType` | [TsgcXAdESType](../types/TsgcXAdESType.md) | `__property TsgcXAdESType * XAdESType;` |
| `TSAClient: IsgcTSAClient` | [IsgcTSAClient](../types/IsgcTSAClient.md) | `__property IsgcTSAClient TSAClient;` |
| `SignatureParentElement: string` | `string` | `__property UnicodeString SignatureParentElement;` |
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

