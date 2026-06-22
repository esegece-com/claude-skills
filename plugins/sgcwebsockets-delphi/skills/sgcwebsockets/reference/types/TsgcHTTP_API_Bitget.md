# TsgcHTTP_API_Bitget

kind: class
unit: sgcHTTP_API_Bitget

## Properties

| Delphi | Type |
| --- | --- |
| `BitgetOptions: TsgcHTTPBitget_Options` | [TsgcHTTPBitget_Options](./TsgcHTTPBitget_Options.md) |
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
function GetServerTime: string;
function GetTickers(const aProductType: string = 'SPOT'; const aSymbol: string = ''): string;
function GetOrderBook(const aSymbol: string; const aProductType: string = 'SPOT'; const aLimit: string = ''): string;
function GetCandles(const aSymbol: string; const aGranularity: string = '1min'; const aProductType: string = 'SPOT'; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 100): string;
function GetRecentTrades(const aSymbol: string; const aProductType: string = 'SPOT'; aLimit: Integer = 100): string;
function PlaceOrder(const aSymbol, aSide, aOrderType, aForce, aSize: string; const aProductType: string = 'SPOT'; const aPrice: string = ''; const aClientOid: string = ''): string;
function CancelOrder(const aSymbol, aOrderId: string; const aProductType: string = 'SPOT'): string;
function GetOpenOrders(const aSymbol: string = ''; const aProductType: string = 'SPOT'): string;
function GetOrderDetail(const aSymbol, aOrderId: string; const aProductType: string = 'SPOT'): string;
function GetOrderHistory(const aSymbol: string; const aProductType: string = 'SPOT'; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 100): string;
function GetAccountAssets(const aProductType: string = 'SPOT'; const aCoin: string = ''): string;
function GetAccountInfo: string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

