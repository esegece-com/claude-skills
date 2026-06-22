# TsgcHTTP_API_MEXC_Futures

kind: class
unit: sgcHTTP_API_MEXC

## Properties

| Delphi | Type |
| --- | --- |
| `MEXCOptions: TsgcHTTPMEXCFutures_Options` | [TsgcHTTPMEXCFutures_Options](./TsgcHTTPMEXCFutures_Options.md) |
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
function GetPing: string;
function GetServerTime: string;
function GetContracts: string;
function GetDepth(const aSymbol: string; aLimit: Integer = 50): string;
function GetDeals(const aSymbol: string; aLimit: Integer = 100): string;
function GetKlines(const aSymbol, aInterval: string; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 200): string;
function GetIndexPrice(const aSymbol: string): string;
function GetFairPrice(const aSymbol: string): string;
function GetFundingRate(const aSymbol: string): string;
function GetAccountAssets: string;
function GetPositionList: string;
function SetPositionLeverage(const aSymbol: string; aLeverage: Integer; const aMarginMode: string = ''): string;
function PlaceOrder(const aSymbol, aSide, aPositionSide, aType: string; aQuantity: Double; aPrice: Double = 0; const aClientOrderId: string = ''; const aExtraParams: string = ''): string;
function CancelOrder(const aSymbol: string; const aOrderId: string = ''; const aClientOrderId: string = ''): string;
function CancelAllOrders(const aSymbol: string): string;
function GetOpenOrders(const aSymbol: string = ''): string;
function GetOrderHistory(const aSymbol: string = ''; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 100): string;
function GetFundingHistory(const aSymbol: string; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 100): string;
function GetAllTickers: string;
function GetFundingRateHistory(const aSymbol: string; aPageNum: Integer = 1; aPageSize: Integer = 20): string;
function GetFairPriceKline(const aSymbol: string; aInterval: string; aStart: Int64 = 0; aEnd: Int64 = 0): string;
function GetIndexPriceKline(const aSymbol: string; aInterval: string; aStart: Int64 = 0; aEnd: Int64 = 0): string;
function GetOpenPositions: string;
function ChangeMargin(const aSymbol: string; aAmount: Double; const aType: string): string;
function GetPositionMode: string;
function ChangePositionMode(const aPositionMode: Integer): string;
function PlaceBatchOrder(const aOrders: string): string;
function GetOrderDetail(const aOrderId: string): string;
function GetOrderDealDetails(const aOrderId: string): string;
function PlaceTriggerOrder(const aSymbol, aSide, aPositionSide, aType: string; aQuantity: Double; aTriggerPrice: Double; aExecutePrice: Double = 0; const aTriggerType: string = ''): string;
function CancelTriggerOrder(const aOrderId: string): string;
function CancelAllTriggerOrders(const aSymbol: string = ''): string;
function GetTriggerOrders(const aSymbol: string = ''; aPageNum: Integer = 1; aPageSize: Integer = 20): string;
function GetStopOrders(const aSymbol: string = ''; aPageNum: Integer = 1; aPageSize: Integer = 20): string;
function CancelStopOrder(const aOrderId: string): string;
function CancelAllStopOrders(const aSymbol: string = ''): string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

