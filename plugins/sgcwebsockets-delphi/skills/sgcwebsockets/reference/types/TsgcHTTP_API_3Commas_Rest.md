# TsgcHTTP_API_3Commas_Rest

kind: class
unit: sgcHTTP_API_ThreeCommas

## Properties

| Delphi | Type |
| --- | --- |
| `ThreeCommas: TsgcHTTPThreeCommas_Options` | [TsgcHTTPThreeCommas_Options](./TsgcHTTPThreeCommas_Options.md) |
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
function GetAccounts: string;
function GetMarketList: string;
function GetMarketPairs(const aMarketCode: string = ''): string;
function GetCurrencyRatesWithLeverageData(const aMarketCode: string; const aPair: string): string;
function GetCurrencyRates(const aMarketCode: string; const aPair: string): string;
function GetBalances(aAccountId: Integer): string;
function GetAccountTableData(aAccountId: Integer): string;
function GetAccountLeverage(aAccountId: Integer; const aPair: string): string;
function GetAccountInfo(aAccountId: Integer): string;
function GetSmartTradeHistory: string;
function CreateSmartTrade(const aOrder: TsgcHTTPThreeCommasOrder): string;
function EditSmartTrade(const aId: Integer; const aOrder: TsgcHTTPThreeCommasOrder): string;
function PlaceMarketOrder(aAccountId: Integer; aOrderSide: TsgcHTTPThreeCommasOrderSide; const aPair: string; aQuantity: Extended): string;
function PlaceLimitOrder(aAccountId: Integer; aOrderSide: TsgcHTTPThreeCommasOrderSide; const aPair: string; aQuantity, aPrice: Extended): string;
function GetSmartTrade(const aId: Integer): string;
function CancelSmartTrade(const aId: Integer): string;
function CloseByMarketSmartTrade(const aId: Integer): string;
function ForceStartSmartTrade(const aId: Integer): string;
function AddFundsSmartTrade(const aId: Integer; const aOrderType: string; aUnits_Amount: Double; aUnit_Price: Double = 0): string;
function GetSmartTradeTrades(const aId: Integer): string;
function CreateDCABot(const aBot: string): string;
function GetDCABot(const aBotId: Integer): string;
function GetDCABots(aLimit: Integer = 50; aOffset: Integer = 0; const aScope: string = ''): string;
function EnableDCABot(const aBotId: Integer): string;
function DisableDCABot(const aBotId: Integer): string;
function DeleteDCABot(const aBotId: Integer): string;
function CancelDCABot(const aBotId: Integer): string;
function GetDCABotStats(const aBotId: Integer): string;
function GetAvailableStrategyList: string;
function GetBlacklistPairs: string;
function AddBlacklistPairs(const aPairs: string): string;
function GetDeals(aLimit: Integer = 50; aOffset: Integer = 0; const aScope: string = ''; const aBotId: string = ''): string;
function GetDeal(const aDealId: Integer): string;
function UpdateDeal(const aDealId: Integer; const aParams: string): string;
function CancelDeal(const aDealId: Integer): string;
function CloseAtMarketDeal(const aDealId: Integer): string;
function CreateGridBot(const aBot: string): string;
function GetGridBot(const aBotId: Integer): string;
function GetGridBots(aLimit: Integer = 50; aOffset: Integer = 0): string;
function EnableGridBot(const aBotId: Integer): string;
function DisableGridBot(const aBotId: Integer): string;
function DeleteGridBot(const aBotId: Integer): string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

