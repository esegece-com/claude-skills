# TsgcHTTP_API_Kucoin_Futures_Rest

kind: class
unit: sgcHTTP_API_Kucoin

## Properties

| Delphi | Type |
| --- | --- |
| `KucoinOptions: TsgcHTTPKucoin_Options` | [TsgcHTTPKucoin_Options](./TsgcHTTPKucoin_Options.md) |
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
function GetAccountOverview(const aCurrency: string = ''): string;
function GetTransactionHistory(aStartAt: Int64 = 0; aEndAt: Int64 = 0; const aType: string = ''; aOffset: Int64 = 0; aMaxCount: Integer = 50; aCurrency: string = ''; aForward: Boolean = True): string;
function PlaceOrder(const aOrder: TsgcHTTPKucoinFuturesOrder): string;
function PlaceMarketOrder(aSide: TsgcHTTPKucoinOrderSide; const aSymbol: string; aSize: Integer; const aLeverage: string = '20'; const aClientOid: string = ''): string;
function PlaceLimitOrder(aSide: TsgcHTTPKucoinOrderSide; const aSymbol: string; aSize: Integer; aPrice: Extended; const aLeverage: string = '20'; const aClientOid: string = ''): string;
function CancelOrder(const aOrderId: string): string;
function LimitOrderMassCancellation(const aSymbol: string): string;
function StopOrderMassCancellation(const aSymbol: string): string;
function GetOrderList: string;
function GetUntriggeredStopOrderList(const aSymbol: string): string;
function GetListOrdersCompleted24hr: string;
function GetOrder(const aOrderId: string): string;
function GetOrderByClientOid(const aClientOid: string): string;
function GetFills(const aOrderId: string = ''; const aSymbol: string = ''; aSide: TsgcHTTPKucoinOrderSide = kosNone; aOrderType: TsgcHTTPKucoinOrderType = kotNone; aStartAt: Int64 = 0; aEndAt: Int64 = 0): string;
function GetRecentFills: string;
function ActiveOrderValueCalculation(const aSymbol: string): string;
function GetPositionDetails(const aSymbol: string): string;
function GetPositionList: string;
function AutoDepositMargin(const aSymbol: string; const aEnabled: Boolean): string;
function AddMarginManually(const aSymbol: string; aMargin: Extended; const aBizNo: string): string;
function ObtainFuturesRiskLimitLevel(const aSymbol: string): string;
function AdjustRiskLimitLevel(const aSymbol: string; aLevel: Integer): string;
function GetFundingHistory(const aSymbol: string): string;
function GetMaxOpenSize(const aSymbol: string; aPrice: Double; aLeverage: Integer = 0): string;
function SwitchMarginMode(const aSymbol: string; const aMarginMode: string): string;
function GetMarginMode(const aSymbol: string): string;
function GetOpenContractList: string;
function GetOrderInfoContract(const aSymbol: string): string;
function GetTicker(const aSymbol: string): string;
function GetPartOrderBook20(const aSymbol: string): string;
function GetPartOrderBook100(const aSymbol: string): string;
function GetFullOrderBook(const aSymbol: string): string;
function GetLevel2PullingMessages(const aSymbol: string; aStartAt: Int64; aEndAt: Int64): string;
function GetTradeHistory(const aSymbol: string): string;
function GetInterestRateList(const aSymbol: string; aStartAt: Int64 = 0; aEndAt: Int64 = 0; aReverse: Boolean = True; aOffset: Int64 = 0; aForward: Boolean = True; aMaxCount: Integer = 10): string;
function GetIndexList(const aSymbol: string; aStartAt: Int64 = 0; aEndAt: Int64 = 0; aReverse: Boolean = True; aOffset: Int64 = 0; aForward: Boolean = True; aMaxCount: Integer = 10): string;
function GetCurrentMarkPrice(const aSymbol: string): string;
function GetPremiumIndex(const aSymbol: string; aStartAt: Int64 = 0; aEndAt: Int64 = 0; aReverse: Boolean = True; aOffset: Int64 = 0; aForward: Boolean = True; aMaxCount: Integer = 10): string;
function GetCurrentFundingRate(const aSymbol: string): string;
function GetKLine(const aSymbol: string; aGranularity: Integer; aFrom: Int64 = 0; aTo: Int64 = 0): string;
function GetServerTime: String;
function GetServiceStatus: String;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

