# TsgcHTTP_API_MEXC_Spot

kind: class
unit: sgcHTTP_API_MEXC

## Properties

| Delphi | Type |
| --- | --- |
| `MEXCOptions: TsgcHTTPMEXC_Options` | [TsgcHTTPMEXC_Options](./TsgcHTTPMEXC_Options.md) |
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
function Ping: Boolean;
function GetServerTime: string;
function GetDefaultSymbols: string;
function GetExchangeInformation: string;
function GetOrderBook(const aSymbol: string; aLimit: Integer = 100): string;
function GetTrades(const aSymbol: string; aLimit: Integer = 100): string;
function GetAggregateTrades(const aSymbol: string; aLimit: Integer = 100; aFromId: Int64 = 0; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetKlines(const aSymbol, aInterval: string; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 500): string;
function GetAveragePrice(const aSymbol: string): string;
function Get24hrTicker(const aSymbol: string = ''): string;
function GetPriceTicker(const aSymbol: string = ''): string;
function GetBookTicker(const aSymbol: string = ''): string;
function NewOrder(const aSymbol, aSide, aType: string; const aTimeInForce: string = ''; aQuantity: Double = 0; aQuoteOrderQty: Double = 0; aPrice: Double = 0; const aClientOrderId: string = ''; aStopPrice: Double = 0; aIcebergQty: Double = 0; const aExtraParams: string = ''): string;
function TestNewOrder(const aSymbol, aSide, aType: string; const aTimeInForce: string = ''; aQuantity: Double = 0; aQuoteOrderQty: Double = 0; aPrice: Double = 0; const aClientOrderId: string = ''; aStopPrice: Double = 0; aIcebergQty: Double = 0; const aExtraParams: string = ''): string;
function CancelOrder(const aSymbol: string; const aOrderId: string = ''; const aClientOrderId: string = ''): string;
function CancelAllOrders(const aSymbol: string): string;
function GetOrder(const aSymbol: string; const aOrderId: string = ''; const aClientOrderId: string = ''): string;
function GetOpenOrders(const aSymbol: string = ''): string;
function GetAllOrders(const aSymbol: string; aLimit: Integer = 500; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetAccountInformation: string;
function GetMyTrades(const aSymbol: string; aLimit: Integer = 500; aFromId: Int64 = 0; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetSubAccounts(const aSubAccount: string = ''; const aIsFreeze: string = ''; aPage: Integer = 1; aLimit: Integer = 50): string;
function GetDepositAddress(const aCoin: string; const aNetwork: string = ''): string;
function GetWithdrawHistory(const aCoin: string = ''; aStatus: Integer = -1; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aOffset: Integer = 0; aLimit: Integer = 0): string;
function Withdraw(const aCoin, aAddress: string; aAmount: Double; const aNetwork: string = ''; const aAddressTag: string = ''; const aWithdrawOrderId: string = ''; const aExtraParams: string = ''): string;
function GetCapitalConfig: string;
function BatchOrders(const aOrders: string): string;
function GetTradeFee(const aSymbol: string): string;
function GetDepositHistory(const aCoin: string = ''; aStatus: Integer = -1; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aOffset: Integer = 0; aLimit: Integer = 0): string;
function CancelWithdraw(const aId: string): string;
function CreateInternalTransfer(const aCoin: string; aAmount: Double; const aFromAccountType, aToAccountType: string): string;
function GetTransferHistory(const aCoin: string = ''; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aPage: Integer = 1; aLimit: Integer = 50): string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

