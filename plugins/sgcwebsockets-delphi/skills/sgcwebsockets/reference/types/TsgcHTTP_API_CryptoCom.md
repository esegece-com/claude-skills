# TsgcHTTP_API_CryptoCom

kind: class
unit: sgcHTTP_API_CryptoCom

## Properties

| Delphi | Type |
| --- | --- |
| `CryptoComOptions: TsgcHTTPCryptoCom_Options` | [TsgcHTTPCryptoCom_Options](./TsgcHTTPCryptoCom_Options.md) |
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
function GetInstruments: string;
function GetTicker(const aInstrumentName: string = ''): string;
function GetOrderBook(const aInstrumentName: string; aDepth: Integer = 10): string;
function GetTrades(const aInstrumentName: string; aCount: Integer = 0): string;
function GetCandlestick(const aInstrumentName: string; const aTimeframe: string = '5m'): string;
function CreateOrder(const aInstrumentName, aSide, aType: string; const aPrice: string = ''; const aQuantity: string = ''; const aNotional: string = ''): string;
function CancelOrder(const aInstrumentName, aOrderId: string): string;
function CancelAllOrders(const aInstrumentName: string): string;
function GetOpenOrders(const aInstrumentName: string = ''): string;
function GetOrderDetail(const aOrderId: string): string;
function GetOrderHistory(const aInstrumentName: string = ''; aStartTs: Int64 = 0; aEndTs: Int64 = 0): string;
function GetAccountSummary(const aCurrency: string = ''): string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

