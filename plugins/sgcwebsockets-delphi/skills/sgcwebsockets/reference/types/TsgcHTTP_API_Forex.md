# TsgcHTTP_API_Forex

kind: class
unit: sgcHTTP_API_Forex

## Properties

| Delphi | Type |
| --- | --- |
| `SessionToken: string (read-only)` | `string` |
| `SessionInfo: TsgcHTTPForex_SessionInfo (read-only)` | [TsgcHTTPForex_SessionInfo](./TsgcHTTPForex_SessionInfo.md) |
| `Options: TsgcHTTPForex_Options` | [TsgcHTTPForex_Options](./TsgcHTTPForex_Options.md) |
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
function LogOn(const aUserName, aPassword, aAppKey: string): string;
function LogOff: Boolean;
function NewTradeOrder(const aMarketId, aTradingAccountId: Int64; const aDirection: string; const aQuantity: Double; const aBidPrice, aOfferPrice: Double; const aAuditId: string) : string;
function CancelOrder(const aOrderId, aTradingAccountId, aMarketId: Int64) : string;
function NewStopLimitOrder(const aMarketId, aTradingAccountId: Int64; const aDirection: TsgcForexDirection; const aQuantity, aTriggerPrice: Double; const aApplicability: TsgcForexApplicability = faGTC): string;
function UpdateTradeOrder(const aOrder: TsgcHTTPForexTradeOrder) : string;
function UpdateStopLimitOrder(const aOrder: TsgcHTTPForexStopLimitOrder) : string;
function ListOpenPositions(const aTradingAccountId: Int64): string;
function ListActiveStopLimitOrders(const aTradingAccountId: Int64): string;
function GetClientAndTradingAccount: string;
function GetOrder(const aOrderId: Int64): string;
function ListTradeHistory(const aTradingAccountId: Int64; aMaxResults: Integer = 100): string;
function ListStopLimitOrderHistory(const aTradingAccountId: Int64; aMaxResults: Integer = 100): string;
function SimulateTrade(const aMarketId, aTradingAccountId: Int64; const aDirection: string; const aQuantity: Double; const aBidPrice, aOfferPrice: Double; const aAuditId: string) : string;
function GetServiceStatus: string;
function Ping: string;
function GetMarketInformation(const aMarketId: Int64): string;
function ListCfdMarkets(const aSearchByMarketName: string; const aMaxResults: Integer = 100): string;
function FullSearchWithTags(const aQuery: string; const aMaxResults: Integer = 100): string;
function GetPriceBars(const aMarketId: Int64; const aInterval: string; const aSpan: Integer; const aPriceBars: Integer): string;
function GetPriceTicks(const aMarketId: Int64; const aPriceTicks: Integer): string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

