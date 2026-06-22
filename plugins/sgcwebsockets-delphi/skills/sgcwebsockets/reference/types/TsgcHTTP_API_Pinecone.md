# TsgcHTTP_API_Pinecone

kind: class
unit: sgcHTTP_API_Pinecone

## Properties

| Delphi | Type |
| --- | --- |
| `PineconeOptions: TsgcHTTPPinecone_Options` | [TsgcHTTPPinecone_Options](./TsgcHTTPPinecone_Options.md) |
| `ReadTimeout: Integer` | `Integer` |
| `TLSOptions: TsgcHTTPTLS_Options` | [TsgcHTTPTLS_Options](./TsgcHTTPTLS_Options.md) |
| `CircuitBreaker: TsgcWSCircuitBreaker` | [TsgcWSCircuitBreaker](./TsgcWSCircuitBreaker.md) |
| `Version: String (read-only)` | `String` |

## Events

| Delphi | Type |
| --- | --- |
| `OnHTTPAPIException: TsgcHTTPAPIExceptionEvent` | [TsgcHTTPAPIExceptionEvent](./TsgcHTTPAPIExceptionEvent.md) |
| `OnHTTPAPISSE: TsgcHTTPAPISSEEvent` | [TsgcHTTPAPISSEEvent](./TsgcHTTPAPISSEEvent.md) |

## Methods

```pascal
function VectorsDescribeIndexStats(const aIndexName, aProjectId: string; const aFilter: TStrings = nil): string;
function VectorsQuery(const aIndexName, aProjectId: string; const aParams: TsgcHTTPPineconeVectorQuery): string;
function VectorsDelete(const aIndexName, aProjectId: string; const aParams: TsgcHTTPPineconeVectorDelete): string;
function VectorsFetch(const aIndexName, aProjectId: string; const aIds: TStrings; const aNamespace: string = ''): string;
function VectorsUpdate(const aIndexName, aProjectId: string; const aParams: TsgcHTTPPineconeVectorUpdate): string;
function VectorsUpsert(const aIndexName, aProjectId: string; const aParams: TsgcHTTPPineconeVectorUpserts): string;
function CollectionsList: string;
function CollectionCreate(const aName, aSource: string): string;
function CollectionDescribe(const aName: string): string;
function CollectionDelete(const aName: string): string;
function IndexesList: string;
function IndexCreate(const aParams: TsgcHTTPPineconeIndexCreate): string;
function IndexDescribe(const aName: string): string;
function IndexDelete(const aName: string): string;
function IndexConfigure(const aName: string; aReplicas: Integer; const aPodType: string): string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

