# TsgcHTTP_API_Deribit

kind: class
unit: sgcHTTP_API_Deribit

## Properties

| Delphi | Type |
| --- | --- |
| `DeribitOptions: TsgcHTTPDeribit_Options` | [TsgcHTTPDeribit_Options](./TsgcHTTPDeribit_Options.md) |
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
function Authenticate: string;
function GetInstruments(const aCurrency: string; const aKind: string = ''): string;
function GetTicker(const aInstrumentName: string): string;
function GetOrderBook(const aInstrumentName: string; aDepth: Integer = 10): string;
function GetTrades(const aInstrumentName: string; aCount: Integer = 10): string;
function GetCurrencies: string;
function GetIndexPrice(const aIndexName: string): string;
function GetFundingRateHistory(const aInstrumentName: string; aStartTimestamp: Int64 = 0; aEndTimestamp: Int64 = 0): string;
function GetFundingRateValue(const aInstrumentName: string; aStartTimestamp: Int64; aEndTimestamp: Int64): string;
function GetBookSummaryByCurrency(const aCurrency: string; const aKind: string = ''): string;
function GetBookSummaryByInstrument( const aInstrumentName: string): string;
function Buy(const aInstrumentName: string; aAmount: Double; const aOrderType: string = 'market'; aPrice: Double = 0): string;
function Sell(const aInstrumentName: string; aAmount: Double; const aOrderType: string = 'market'; aPrice: Double = 0): string;
function CancelOrder(const aOrderId: string): string;
function CancelAllOrders: string;
function CancelAllByInstrument(const aInstrumentName: string): string;
function EditOrder(const aOrderId: string; aAmount: Double; aPrice: Double): string;
function GetOpenOrders(const aCurrency: string; const aKind: string = ''): string;
function GetOrderState(const aOrderId: string): string;
function GetOrderHistory(const aCurrency: string; const aKind: string = ''; aCount: Integer = 20; aOffset: Integer = 0): string;
function GetPositions(const aCurrency: string; const aKind: string = ''): string;
function GetAccountSummary(const aCurrency: string; aExtended: Boolean = False): string;
function GetSubAccounts(aWithPortfolio: Boolean = False): string;
function GetTransactionLog(const aCurrency: string; aStartTimestamp: Int64 = 0; aEndTimestamp: Int64 = 0; aCount: Integer = 20): string;
function GetDeposits(const aCurrency: string; aCount: Integer = 10; aOffset: Integer = 0): string;
function GetWithdrawals(const aCurrency: string; aCount: Integer = 10; aOffset: Integer = 0): string;
function GetTransfers(const aCurrency: string; aCount: Integer = 10; aOffset: Integer = 0): string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

