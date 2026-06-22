# TsgcHTTP_API_Binance_Futures_Rest

kind: class
unit: sgcHTTP_API_Binance

## Properties

| Delphi | Type |
| --- | --- |
| `FuturesContracts: TsgcHTTPBinanceFuturesContracts` | [TsgcHTTPBinanceFuturesContracts](./TsgcHTTPBinanceFuturesContracts.md) |
| `BinanceOptions: TsgcHTTPBinance_Options` | [TsgcHTTPBinance_Options](./TsgcHTTPBinance_Options.md) |
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
function GetMarkPrice(const aSymbol: String = ''): string;
function GetFundingRateHistory(const aSymbol: String; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 100): string;
function GetOpenInterest(const aSymbol: String = ''): string;
function GetOpenInterestStatistics(const aSymbol: String; const aPeriod: TsgcHTTPBinanceFutOpenInterestPeriods; aLimit: Integer = 30; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetTopTraderAccountRatio(const aSymbol: String; const aPeriod: TsgcHTTPBinanceFutOpenInterestPeriods; aLimit: Integer = 30; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetTopTraderPositionRatio(const aSymbol: String; const aPeriod: TsgcHTTPBinanceFutOpenInterestPeriods; aLimit: Integer = 30; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetGlobalAccountRatio(const aSymbol: String; const aPeriod: TsgcHTTPBinanceFutOpenInterestPeriods; aLimit: Integer = 30; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetTakerVolume(const aSymbol: String; const aPeriod: TsgcHTTPBinanceFutOpenInterestPeriods; aLimit: Integer = 30; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetContinuousKLines(const aPair, aContractType: String; const aInterval: TsgcHTTPBinanceChartIntervals; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 500): string;
function GetIndexPriceKLines(const aPair: String; const aInterval: TsgcHTTPBinanceChartIntervals; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 500): string;
function GetMarkPriceKLines(const aSymbol: String; const aInterval: TsgcHTTPBinanceChartIntervals; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 500): string;
function GetPremiumIndexKLines(const aSymbol: String; const aInterval: TsgcHTTPBinanceChartIntervals; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 500): string;
function GetFundingInfo: string;
function GetPriceTickerV2(const aSymbol: String = ''): string;
function GetIndexInfo(const aSymbol: String = ''): string;
function GetAssetIndex(const aSymbol: String = ''): string;
function GetConstituents(const aSymbol: String): string;
function GetDeliveryPrice(const aPair: String): string;
function GetBasis(const aPair, aContractType: String; const aPeriod: TsgcHTTPBinanceFutOpenInterestPeriods; aLimit: Integer = 30; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function ChangePositionMode(aDualPosition: Boolean): string;
function GetCurrentPositionMode: string;
function NewOrder(const aSymbol, aSide: String; aPositionSide: String; const aType: String; aTimeInForce: String = ''; aQuantity: Double = 0; aReduceOnly: string = ''; aPrice: Double = 0; aNewClientOrderId: String = ''; aStopPrice: Double = 0; aClosePosition: string = ''; aActivationPrice: Double = 0; aCallbackRate: Double = 0; aWorkingType: String = ''; aNewOrderRespType: String = ''; aPriceMatch: String = ''; aSelfTradePreventionMode: String = ''; aGoodTillDate: Int64 = 0; aPriceProtect: String = ''): String;
function PlaceMarketOrder(aSide: TsgcHTTPBinanceOrderSide; const aSymbol: string; aQuantity: Double): string;
function PlaceLimitOrder(aSide: TsgcHTTPBinanceOrderSide; const aSymbol: string; aQuantity: Double; aLimitPrice: Double): string;
function PlaceStopOrder(aSide: TsgcHTTPBinanceOrderSide; const aSymbol: string; aQuantity, aStopPrice, aLimitPrice: Double): string;
function PlaceTrailingStopOrder(aSide: TsgcHTTPBinanceOrderSide; const aSymbol: string; aQuantity, aActivationPrice, aCallbackRate: Double): string;
function QueryOrder(const aSymbol: String; aOrderId: Int64 = 0; const aOrigClientOrderId: String = ''): string;
function CancelOrder(const aSymbol: String; aOrderId: Int64 = 0; const aOrigClientOrderId: String = ''): string;
function CancelAllOpenOrders(const aSymbol: String): string;
function AutoCancelAllOpenOrders(const aSymbol: String; aCountdownTime: Integer): string;
function QueryCurrentOpenOrder(const aSymbol: String; aOrderId: Int64 = 0; const aOrigClientOrderId: String = ''): string;
function GetOpenOrders(const aSymbol: String = ''): string;
function GetAllOrders(const aSymbol: String; aOrderId: Int64 = 0; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 100): string;
function TestNewOrder(const aSymbol, aSide: String; aPositionSide: String; const aType: String; aTimeInForce: String = ''; aQuantity: Double = 0; aReduceOnly: string = ''; aPrice: Double = 0; aNewClientOrderId: String = ''; aStopPrice: Double = 0; aClosePosition: string = ''; aActivationPrice: Double = 0; aCallbackRate: Double = 0; aWorkingType: String = ''; aNewOrderRespType: String = ''): String;
function ModifyOrder(const aSymbol: String; aOrderId: Int64 = 0; const aOrigClientOrderId: String = ''; aSide: String = ''; aQuantity: Double = 0; aPrice: Double = 0; aPriceMatch: String = ''): String;
function NewBatchOrders(const aBatchOrders: String): String;
function ModifyBatchOrders(const aBatchOrders: String): String;
function CancelBatchOrders(const aSymbol: String; const aOrderIdList: String = ''; const aOrigClientOrderIdList: String = ''): String;
function GetOrderAmendment(const aSymbol: String; aOrderId: Int64 = 0; const aOrigClientOrderId: String = ''; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 50): String;
function CountdownCancelAll(const aSymbol: String; aCountdownTime: Integer): string;
function GetForceOrders(const aSymbol: String = ''; aAutoCloseType: String = ''; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 50): string;
function GetADLQuantile(const aSymbol: String = ''): string;
function GetAccountBalance: string;
function GetAccountInformation: string;
function ChangeInitialLeverage(const aSymbol: String; aLeverage: Integer): string;
function ChangeMarginType(const aSymbol, aMarginType: String): string;
function ModifyIsolatedPositionMargin(const aSymbol: String; aAmount: Double; aType: Integer; aPositionSide: String = ''): string;
function GetPositionMarginChangeHistory(const aSymbol: String; aType: Integer = 0; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 500): string;
function GetPositionInformation(const aSymbol: String = ''): string;
function GetAccountTradeList(const aSymbol: String; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aFromId: Integer = 0; aLimit: Integer = 500): String;
function GetIncomeHistory(const aSymbol: String = ''; const aIncomeType: String = ''; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 100): string;
function GetNotionalLeverageBracket(const aSymbol: String = ''): string;
function GetAccountBalanceV3: string;
function GetAccountInformationV3: string;
function GetPositionInformationV3(const aSymbol: String = ''): string;
function GetCommissionRate(const aSymbol: String): string;
function GetAccountConfig: string;
function GetSymbolConfig(const aSymbol: String = ''): string;
function GetOrderRateLimit: string;
function GetApiTradingStatus(const aSymbol: String = ''): string;
function ChangeMultiAssetsMode(aMultiAssetsMargin: Boolean): string;
function GetMultiAssetsMode: string;
function SetFeeBurn(aFeeBurn: Boolean): string;
function GetFeeBurn: string;
function CreateListenKey: string;
function KeepAliveListenKey: string;
function CloseListenKey: string;
function Ping: Boolean;
function GetServerTime: String;
function GetExchangeInformation: String;
function GetOrderBook(const aSymbol: String; aLimit: Integer = 100): string;
function GetTrades(const aSymbol: String; aLimit: Integer = 500): string;
function GetHistoricalTrades(const aSymbol: String; aLimit: Integer = 500; aFromId: Integer = 0): string;
function GetAggregateTrades(const aSymbol: String; aFromId: Integer = 0; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 500): String;
function GetKLines(const aSymbol: String; aInterval: TsgcHTTPBinanceChartIntervals; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 500): String;
function Get24hrTicker(const aSymbol: String): string;
function GetPriceTicker(const aSymbol: String = ''): string;
function GetPriceTickers(const aSymbols: String = ''): string;
function GetBookTicker(const aSymbol: String = ''): string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

