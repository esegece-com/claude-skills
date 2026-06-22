# TsgcAI_OpenAI_Embeddings

kind: class
unit: sgcAI_OpenAI_Embeddings

## Properties

| Delphi | Type |
| --- | --- |
| `EmbeddingsOptions: TsgcOpenAI_Embeddings_Options` | [TsgcOpenAI_Embeddings_Options](./TsgcOpenAI_Embeddings_Options.md) |
| `Database: TsgcAI_Database_Vector` | [TsgcAI_Database_Vector](./TsgcAI_Database_Vector.md) |
| `OpenAIOptions: TsgcHTTPOpenAI_Options` | [TsgcHTTPOpenAI_Options](./TsgcHTTPOpenAI_Options.md) |
| `Version: String (read-only)` | `String` |

## Events

| Delphi | Type |
| --- | --- |
| `OnCreateEmbeddingsStart: TsgcOpenAICreateEmbeddingsStart` | [TsgcOpenAICreateEmbeddingsStart](./TsgcOpenAICreateEmbeddingsStart.md) |
| `OnCreateEmbeddingsProgress: TsgcOpenAICreateEmbeddingsProgress` | [TsgcOpenAICreateEmbeddingsProgress](./TsgcOpenAICreateEmbeddingsProgress.md) |
| `OnCreateEmbeddingsStop: TsgcOpenAICreateEmbeddingsStop` | [TsgcOpenAICreateEmbeddingsStop](./TsgcOpenAICreateEmbeddingsStop.md) |
| `OnAfterCreateEmbedding: TsgcOpenAIAfterCreateEmbedding` | [TsgcOpenAIAfterCreateEmbedding](./TsgcOpenAIAfterCreateEmbedding.md) |
| `OnBeforeCreateEmbedding: TsgcOpenAIBeforeCreateEmbedding` | [TsgcOpenAIBeforeCreateEmbedding](./TsgcOpenAIBeforeCreateEmbedding.md) |

## Methods

```pascal
procedure CreateEmbeddings(const aInput: string);
procedure CreateEmbeddingsFromFile(const aFileName: string);
function GetEmbedding(const aInput, aParams: string): string;
```

