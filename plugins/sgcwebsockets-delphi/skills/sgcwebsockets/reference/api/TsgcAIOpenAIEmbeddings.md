# TsgcAIOpenAIEmbeddings

unit: sgcAI

Add `sgcAI` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Database: TsgcAI_Database_Vector` | [TsgcAI_Database_Vector](../types/TsgcAI_Database_Vector.md) | `__property TsgcAI_Database_Vector * Database;` |
| `OpenAIOptions: TsgcHTTPOpenAI_Options` | [TsgcHTTPOpenAI_Options](../types/TsgcHTTPOpenAI_Options.md) | `__property TsgcHTTPOpenAI_Options * OpenAIOptions;` |
| `EmbeddingsOptions: TsgcOpenAI_Embeddings_Options` | [TsgcOpenAI_Embeddings_Options](../types/TsgcOpenAI_Embeddings_Options.md) | `__property TsgcOpenAI_Embeddings_Options * EmbeddingsOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnCreateEmbeddingsStart: TsgcOpenAICreateEmbeddingsStart` | [TsgcOpenAICreateEmbeddingsStart](../types/TsgcOpenAICreateEmbeddingsStart.md) | `__property TsgcOpenAICreateEmbeddingsStart * OnCreateEmbeddingsStart;` |
| `OnCreateEmbeddingsProgress: TsgcOpenAICreateEmbeddingsProgress` | [TsgcOpenAICreateEmbeddingsProgress](../types/TsgcOpenAICreateEmbeddingsProgress.md) | `__property TsgcOpenAICreateEmbeddingsProgress * OnCreateEmbeddingsProgress;` |
| `OnCreateEmbeddingsStop: TsgcOpenAICreateEmbeddingsStop` | [TsgcOpenAICreateEmbeddingsStop](../types/TsgcOpenAICreateEmbeddingsStop.md) | `__property TsgcOpenAICreateEmbeddingsStop * OnCreateEmbeddingsStop;` |
| `OnBeforeCreateEmbedding: TsgcOpenAIBeforeCreateEmbedding` | [TsgcOpenAIBeforeCreateEmbedding](../types/TsgcOpenAIBeforeCreateEmbedding.md) | `__property TsgcOpenAIBeforeCreateEmbedding * OnBeforeCreateEmbedding;` |
| `OnAfterCreateEmbedding: TsgcOpenAIAfterCreateEmbedding` | [TsgcOpenAIAfterCreateEmbedding](../types/TsgcOpenAIAfterCreateEmbedding.md) | `__property TsgcOpenAIAfterCreateEmbedding * OnAfterCreateEmbedding;` |

## Methods

Delphi

```pascal
procedure CreateEmbeddings(const aInput: string);
procedure CreateEmbeddingsFromFile(const aFileName: string);
function GetEmbedding(const aInput, aParams: string): string;
```

C++Builder

```cpp
void __fastcall CreateEmbeddings(const UnicodeString aInput);
void __fastcall CreateEmbeddingsFromFile(const UnicodeString aFileName);
UnicodeString __fastcall GetEmbedding(const UnicodeString aInput, const UnicodeString aParams);
```

