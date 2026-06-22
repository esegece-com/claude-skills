# TsgcHTTP_API_Kraken_Rest

kind: class
unit: sgcHTTP_API_Kraken

## Properties

| Delphi | Type |
| --- | --- |
| `KrakenOptions: TsgcHTTPKraken_Options` | [TsgcHTTPKraken_Options](./TsgcHTTPKraken_Options.md) |
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
function GetWebSocketsToken: String;
function GetSystemStatus: String;
function GetServerTime: String;
function GetAssets(const aInfo: String = ''; const aClass: String = ''; const aAsset: String = ''): String;
function GetAssetPairs(const aPairs: Array of String; const aInfo: String = ''; const aLeverage: String = ''; const aFees: String = ''; const aMargin: String = ''): String;
function GetTicker(const aPairs: Array of String): String;
function GetOHLC(const aPair: String; aInterval: TsgcHTTPKrakenInterval = kinh1min; aSince: String = ''): String;
function GetOrderBook(const aPair: String; aCount: Integer = 0): String;
function GetTrades(const aPair: String; aSince: String = ''): String;
function GetSpread(const aPair: String; aSince: String = ''): String;
function GetAccountBalance: String;
function GetExtendedBalance: String;
function GetTradeBalance(const aClass: String = ''; const aAsset: String = ''): String;
function GetOpenOrders(const aTrades: Boolean = False; const aUserRef: String = ''): String;
function GetClosedOrders(const aTrades: Boolean = False; const aUserRef: String = ''; const aStart: String = ''; const aEnd: String = ''; const aOfs: String = ''; const aCloseTime: String = ''): String;
function QueryOrders(const aTxId: String; const aTrades: Boolean = False; const aUserRef: String = ''): String;
function GetTradesHistory(const aType: String = 'all'; const aTrades: Boolean = False; const aStart: String = ''; const aEnd: String = ''; const aOfs: String = ''): String;
function QueryTrades(const aTxId: String; const aTrades: Boolean = False): String;
function GetOpenPositions(const aTxId: String; const aDocalcs: Boolean = False; const aConsolidation: String = ''): String;
function GetLedgers(const aClass: String = ''; const aAsset: String = ''; const aType: String = 'all'; const aStart: String = ''; const aEnd: String = ''; const aOfs: String = ''): String;
function QueryLedgers(const aId: String): String;
function GetTradeVolume(const aPair: String = ''; const aFeeInfo: String = ''): String;
function AddExport(const aDescription: String; const aReport: String = 'trades'; const aFormat: String = 'CSV'; const aFields: String = 'all'; const aAsset: String = 'all'; const aStartTm: String = ''; const aEndTm: String = ''): String;
function ExportStatus(const aReport: String = 'trades'): String;
function RetrieveExport(const aId: String): String;
function RemoveExport(const aId: String; const aType: String = CS_HTTP_METHOD_DELETE): String;
function AddOrder(const aOrder: TsgcHTTPKrakenOrder): String;
function AmendOrder(const aOrderId: string; aVolume: Double = 0; aPrice: Double = 0; const aNewUserRef: string = ''): String;
function CancelOrder(const aTxId: String): String;
function CancelAllOrders: String;
function CancelAllOrdersAfter(aTimeout: Integer): String;
function EditOrder(const aOrderId: string; aVolume: Double = 0; aPrice: Double = 0; const aPair: string = ''; const aNewUserRef: string = ''): String;
function AddOrderBatch(const aOrders: string; const aPair: string = ''): String;
function CancelOrderBatch(const aOrders: string): String;
function GetDepositMethods(const aAsset: string): String;
function GetDepositAddresses(const aAsset: string; aMethod: string; aNew: Boolean = False; aAmount: String = ''): String;
function GetStatusOfRecentDeposits(const aAsset: string = ''; aMethod: string = ''): String;
function GetWithdrawalInformation(const aAsset, aKey, aAmount: string): String;
function WithdrawFunds(const aAsset, aKey, aAmount: string; const aAddress: string = ''): String;
function GetStatusOfRecentWithdraws(const aAsset: string = ''; aMethod: string = ''): String;
function RequestWithdrawalCancelation(const aAsset, aRefId: string): String;
function RequestWalletTransfer(const aAsset, aFrom, aTo, aAmount: string): String;
function GetWithdrawalMethods(const aAsset: string = ''): String;
function GetWithdrawalAddresses(const aAsset: string = ''): String;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

