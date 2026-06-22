# TsgcAIDatabaseVectorPinecone

unit: sgcAI
Edition: Enterprise

Add `sgcAI` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `PineconeOptions: TsgcHTTPPinecone_Options` | [TsgcHTTPPinecone_Options](../types/TsgcHTTPPinecone_Options.md) | `__property TsgcHTTPPinecone_Options * PineconeOptions;` |
| `PineconeIndexOptions: TsgcAIDBVectorPineconeIndex_Options` | [TsgcAIDBVectorPineconeIndex_Options](../types/TsgcAIDBVectorPineconeIndex_Options.md) | `__property TsgcAIDBVectorPineconeIndex_Options * PineconeIndexOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnBeginAddData: TsgcAIOnBeginAddData` | [TsgcAIOnBeginAddData](../types/TsgcAIOnBeginAddData.md) | `__property TsgcAIOnBeginAddData * OnBeginAddData;` |

## Methods

Delphi

```pascal
procedure BeginAddData;
procedure EndAddData;
procedure AddData(const aInput, aVector: string);
function QueryData(const aVector: string): string;
```

C++Builder

```cpp
void __fastcall BeginAddData();
void __fastcall EndAddData();
void __fastcall AddData(const UnicodeString aInput, const UnicodeString aVector);
UnicodeString __fastcall QueryData(const UnicodeString aVector);
```

