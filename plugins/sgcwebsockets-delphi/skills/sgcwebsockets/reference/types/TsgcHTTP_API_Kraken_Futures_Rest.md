# TsgcHTTP_API_Kraken_Futures_Rest

kind: class
unit: sgcHTTP_API_Kraken

## Properties

| Delphi | Type |
| --- | --- |
| `KrakenOptions: TsgcHTTPKrakenFutures_Options` | [TsgcHTTPKrakenFutures_Options](./TsgcHTTPKrakenFutures_Options.md) |
| `FormatExtended: String` | `String` |
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
function GetFeeSchedules: string;
function GetOrderBook(const aSymbol: string): string;
function GetTickers: string;
function GetInstruments: string;
function GetHistory(const aSymbol: string; aLastTime: String = ''): string;
function EditOrderByOrderId(const aOrderId: string; aSize: Integer = 0; aLimitPrice: Double = 0; aStopPrice: Double = 0): string;
function EditOrderByCliOrderId(const aCliOrderId: string; aSize: Integer = 0; aLimitPrice: Double = 0; aStopPrice: Double = 0): string;
function SendOrder(const aOrder: TsgcHTTPKrakenFuturesOrder): string;
function SendMarketOrder(aSide: TsgcHTTPKrakenFuturesOrderSide; const aSymbol: string; aSize: Integer): string;
function SendLimitOrder(aSide: TsgcHTTPKrakenFuturesOrderSide; const aSymbol: string; aSize: Integer; aLimitPrice: Double): string;
function SendStopOrder(aSide: TsgcHTTPKrakenFuturesOrderSide; const aSymbol: string; aSize: Integer; aStopPrice, aLimitPrice: Double): string;
function SendTakeProfit(aSide: TsgcHTTPKrakenFuturesOrderSide; const aSymbol: string; aSize: Integer; aStopPrice, aLimitPrice: Double): string;
function CancelOrderByOrderId(const aOrderId: string): string;
function CancelOrderByCliOrderId(const aCliOrderId: string): string;
function GetFills(const aLastFillDate: string = ''): string;
function Transfer(const aFromAccount, aToAccount, aUnit: string; aAmount: Double): string;
function GetOpenPositions: string;
function GetNotifications: string;
function GetAccounts: string;
function CancelAllOrders(const aSymbol: string = ''): string;
function CancelAllOrdersAfter(aTimeout: Integer = 0): string;
function GetOpenOrders: string;
function GetHistoricalOrders(aSince: TDateTime; aBefore: TDateTime = 0; aSort: string = 'desc'; aContinuationToken: string = ''): string;
function GetHistoricalTriggers(aSince: TDateTime; aBefore: TDateTime = 0; aSort: string = 'desc'; aContinuationToken: string = ''): string;
function GetHistoricalExecutions(aSince: TDateTime; aBefore: TDateTime = 0; aSort: string = 'desc'; aContinuationToken: string = ''): string;
function WalletTransfer(aAmount: Double; const aFromAccount, aToAccount, aUnit: string): string;
function SubAccountTransfer(aAmount: Double; const aFromAccount, aFromUser, aToAccount, aToUser, aUnit: string): string;
function WithdrawalToSpotWallet(const aCurrency: string; aAmount: Double; aSourceWallet: string = 'cash'): string;
function GetFeeScheduleVolumes: string;
function GetAccountLogCSV: string;
function BatchOrder(const aJson: string): string;
function GetOrderStatus(const aOrderIds: string): string;
function GetPNLCurrencyPreferences: string;
function SetPNLCurrencyPreference(const aSymbol, aCurrency: string): string;
function GetLeverageSettings(const aSymbol: string = ''): string;
function SetLeverageSettings(const aSymbol: string; aMaxLeverage: Double): string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

