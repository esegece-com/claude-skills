# TsgcHTTP_API_GateIO

kind: class
unit: sgcHTTP_API_GateIO

## Properties

| Delphi | Type |
| --- | --- |
| `GateIOOptions: TsgcHTTPGateIO_Options` | [TsgcHTTPGateIO_Options](./TsgcHTTPGateIO_Options.md) |
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
function GetCurrencyPairs(const aCurrencyPair: string = ''): string;
function GetTickers(const aCurrencyPair: string = ''): string;
function GetOrderBook(const aCurrencyPair: string; const aInterval: string = '0'; aLimit: Integer = 10): string;
function GetCandlesticks(const aCurrencyPair: string; const aInterval: string = '1m'; aLimit: Integer = 100): string;
function GetTrades(const aCurrencyPair: string; aLimit: Integer = 100): string;
function PlaceOrder(const aCurrencyPair, aSide, aAmount: string; const aPrice: string = ''; const aType: string = 'limit'; const aAccount: string = 'spot'; const aTimeInForce: string = 'gtc'): string;
function CancelOrder(const aOrderId, aCurrencyPair: string): string;
function GetOrder(const aOrderId, aCurrencyPair: string): string;
function GetOpenOrders(const aCurrencyPair: string = ''; aLimit: Integer = 100; const aAccount: string = 'spot'): string;
function GetSpotAccounts(const aCurrency: string = ''): string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

