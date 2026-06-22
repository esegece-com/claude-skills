# TsgcHTTP_API_Bitstamp_Rest

kind: class
unit: sgcHTTP_API_Bitstamp

## Properties

| Delphi | Type |
| --- | --- |
| `BitstampOptions: TsgcHTTPBitstamp_Options` | [TsgcHTTPBitstamp_Options](./TsgcHTTPBitstamp_Options.md) |
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
function GetCurrencies: string;
function GetAllCurrencyPairsTickers: string;
function GetCurrencyPairTicker(const aCurrencyPair: string): string;
function GetHourlyTicker(const aCurrencyPair: string): string;
function GetOrderBook(const aCurrencyPair: string; aGroup: Integer = 0): string;
function GetTransactions(const aCurrencyPair: string; const aTime: string = 'minute'): string;
function GetEURUSDConversionRate: string;
function GetOLHCData(const aCurrencyPair: string; const aStep: TsgcHTTPBitstampOLHC; aLimit: Integer = 1000; aStart: Integer = -1; aEnd: Integer = -1; aExcludeCurrentCandle: Boolean = False): string;
function GetTradingPairsInfo: string;
function GetAccountBalances: string;
function GetAccountBalanceForCurrency(const aCurrency: string): string;
function BuyInstantOrder(const aCurrencyPair: string; const aAmount: String; const aClientId: string = ''): string;
function BuyMarketOrder(const aCurrencyPair: string; const aAmount: String; const aClientId: string = ''): string;
function BuyLimitOrder(const aCurrencyPair, aAmount, aPrice: string; const aClientId: string = ''): string;
function CancelAllOrders: string;
function CancelAllOrdersForCurrencyPair(const aCurrencyPair : string): string;
function CancelOrder(const aOrderId: string): string;
function GetTradingPairs: string;
function GetAllOpenOrders: string;
function GetOpenOrders(const aCurrencyPair: string): string;
function GetOrderStatus(const aId: string; const aClientId: string; aOmitTransactions: Boolean = False): string;
function SellInstantOrder(const aCurrencyPair: string; const aAmount: String; const aClientId: string = ''): string;
function SellMarketOrder(const aCurrencyPair: string; const aAmount: String; const aClientId: string = ''): string;
function SellLimitOrder(const aCurrencyPair, aAmount, aPrice: string; const aClientId: string = ''): string;
function RippleIOUWithdrawal(const aAddress, aAmount: string): string;
function WithdrawalRequests(const aId: string; aLimit: Integer = 1000; aOffset: Integer = 0; const aTimeDelta: Integer = 50000000): string;
function CancelBankOrCryptoWithdrawal(const aId: string): string;
function OpenBankWithdrawal(const aWithdrawal : TsgcHTTPBitstampWithdrawal): string;
function FiatWithdrawalStatus(const aId: string): string;
function CryptoWithdrawal(const aCurrency, aAddress, aAmount, aDestinationTag: string; const aMemoId: string = ''): string;
function GetUserTransactions(aLimit: Integer = 100; aOffset: Integer = 0; const aSort: string = 'desc'): string;
function GetUserTransactionsForCurrencyPair(const aCurrencyPair: string; aLimit: Integer = 100; aOffset: Integer = 0; const aSort: string = 'desc'): string;
function GetTradingFees: string;
function GetTradingFeesForCurrencyPair(const aCurrencyPair: string): string;
function GetWithdrawalFees: string;
function GetCryptoDepositAddress(const aCurrency: string): string;
function TransferToMain(const aCurrency: string; const aAmount: string; const aSubAccountId: string = ''): string;
function TransferFromMain(const aCurrency: string; const aAmount: string; const aSubAccountId: string = ''): string;
function EarnSubscribe(const aCurrency: string; const aAmount: string): string;
function EarnUnsubscribe(const aCurrency: string; const aAmount: string): string;
function GetEarnSubscriptions: string;
function GetEarnTransactions: string;
function GetTravelRuleVASPs: string;
function GetMarkets: string;
function GetWebSocketsToken: string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

