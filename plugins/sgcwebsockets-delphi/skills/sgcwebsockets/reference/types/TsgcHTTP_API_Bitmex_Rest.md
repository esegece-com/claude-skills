# TsgcHTTP_API_Bitmex_Rest

kind: class
unit: sgcHTTP_API_Bitmex

## Properties

| Delphi | Type |
| --- | --- |
| `BitmexOptions: TsgcHTTPBitmex_Options` | [TsgcHTTPBitmex_Options](./TsgcHTTPBitmex_Options.md) |
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
function GetExecutions(const aSymbol: string = ''; const aFilter: string = ''; const aColumns: string = ''; aCount: Integer = 100; aStart: Int64 = 0; aReverse: Boolean = False; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetExecutionsTradeHistory(const aSymbol: string = ''; const aFilter: string = ''; const aColumns: string = ''; aCount: Integer = 100; aStart: Int64 = 0; aReverse: Boolean = False; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetInstruments(const aSymbol: string = ''; const aFilter: string = ''; const aColumns: string = ''; aCount: Integer = 100; aStart: Int64 = 0; aReverse: Boolean = False; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetInstrumentsActive: string;
function GetOrders(const aSymbol: string; const aFilter: string = ''; const aColumns: string = ''; aCount: Integer = 100; aStart: Int64 = 0; aReverse: Boolean = False; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function PlaceOrder(const aOrder: TsgcHTTPBitmexOrder): string;
function PlaceMarketOrder(aSide: TsgcHTTPBitmexOrderSide; const aSymbol: string; aQuantity: Extended): string;
function PlaceLimitOrder(aSide: TsgcHTTPBitmexOrderSide; const aSymbol: string; aQuantity, aPrice: Extended; aHidden: Boolean = True): string;
function PlaceStopOrder(aSide: TsgcHTTPBitmexOrderSide; const aSymbol: string; aQuantity, aStopPrice: Extended): string;
function PlaceStopLimitOrder(aSide: TsgcHTTPBitmexOrderSide; const aSymbol: string; aQuantity, aStopPrice, aLimitPrice: Extended): string;
function AmendOrder(const aOrder: TsgcHTTPBitmexAmendOrder): string;
function CancelOrder(const aOrderId, aClOrderId: string; const aText: string = ''): string;
function CancelAllOrders(const aSymbol: string = ''; const aFilter: string = ''; const aText: string = ''): string;
function CancelAllOrdersAfter(aTimeout: Integer): string;
function ClosePosition(const aSymbol: string; aPrice: Extended = 0): string;
function GetOrderBook(const aSymbol: string; aDepth: Integer = 25): string;
function GetPosition(const aColumns: string = ''; aCount: Integer = 100): string;
function SetPositionIsolate(const aSymbol: string; aEnabled: Boolean): string;
function SetPositionLeverage(const aSymbol: string; aLeverage: Double): string;
function SetPositionRiskLimit(const aSymbol: string; aRiskLimit: Double): string;
function SetPositionTransferMargin(const aSymbol: string; aAmount: Extended): string;
function GetQuotes(const aSymbol: string; const aFilter: string = ''; const aColumns: string = ''; aCount: Integer = 100; aStart: Int64 = 0; aReverse: Boolean = False; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetTrades(const aSymbol: string; const aFilter: string = ''; const aColumns: string = ''; aCount: Integer = 100; aStart: Int64 = 0; aReverse: Boolean = False; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetTradeBucketed(const aBinSize: string; const aSymbol: string = ''; const aFilter: string = ''; const aColumns: string = ''; aCount: Integer = 100; aStart: Int64 = 0; aReverse: Boolean = False; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aPartial: Boolean = False): string;
function GetFunding(const aSymbol: string = ''; const aFilter: string = ''; const aColumns: string = ''; aCount: Integer = 100; aStart: Int64 = 0; aReverse: Boolean = False; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetInsurance(const aFilter: string = ''; const aColumns: string = ''; aCount: Integer = 100; aStart: Int64 = 0; aReverse: Boolean = False): string;
function GetQuoteBucketed(const aBinSize: string; const aSymbol: string = ''; const aFilter: string = ''; const aColumns: string = ''; aCount: Integer = 100; aStart: Int64 = 0; aReverse: Boolean = False; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aPartial: Boolean = False): string;
function GetSettlement(const aSymbol: string = ''; const aFilter: string = ''; const aColumns: string = ''; aCount: Integer = 100; aStart: Int64 = 0; aReverse: Boolean = False; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetLiquidation(const aSymbol: string = ''; const aFilter: string = ''; const aColumns: string = ''; aCount: Integer = 100; aStart: Int64 = 0; aReverse: Boolean = False; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetInstrumentIndices: string;
function GetInstrumentCompositeIndex(const aSymbol: string = ''; const aFilter: string = ''; const aColumns: string = ''; aCount: Integer = 100; aStart: Int64 = 0; aReverse: Boolean = False; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetStats: string;
function GetStatsHistory: string;
function GetStatsHistoryUSD: string;
function GetUserMargin(const aCurrency: string = ''): string;
function GetUserWallet(const aCurrency: string = ''): string;
function GetUserWalletHistory(const aCurrency: string = ''; aCount: Integer = 100; aStart: Int64 = 0; const aTargetAccountId: string = ''; aReverse: Boolean = False): string;
function GetUserWalletSummary(const aCurrency: string = ''): string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

