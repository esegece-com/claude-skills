# TsgcHTTP_API_Binance_Rest

kind: class
unit: sgcHTTP_API_Binance

## Properties

| Delphi | Type |
| --- | --- |
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
function GetAveragePrice(const aSymbol: String): string;
function GetUIKLines(const aSymbol: String; aInterval: TsgcHTTPBinanceChartIntervals; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 500): String;
function GetRollingWindowTicker(const aSymbol: String = ''; const aSymbols: String = ''; const aWindowSize: String = ''): String;
function GetTradingDayTicker(const aSymbol: String = ''; const aSymbols: String = ''; const aType: String = ''): String;
function NewOrder(const aSymbol, aSide, aType: String; aTimeInForce: String = ''; aQuantity: Double = 0; aQuoteOrderQty: Double = 0; aPrice: Double = 0; aNewClientOrderId: String = ''; aStopPrice: Double = 0; aIcebergQty: Double = 0; aTrailingDelta: Int64 = 0; aNewOrderRespType: String = ''; aSelfTradePreventionMode: String = ''; aStrategyId: Int64 = 0; aStrategyType: Integer = 0): String;
function PlaceMarketOrder(aSide: TsgcHTTPBinanceOrderSide; const aSymbol: string; aQuantity: Double): string;
function PlaceMarketQuoteOrder(aSide: TsgcHTTPBinanceOrderSide; const aSymbol: string; aQuoteOrderQty: Double): string;
function PlaceLimitOrder(aSide: TsgcHTTPBinanceOrderSide; const aSymbol: string; aQuantity: Double; aLimitPrice: Double): string;
function PlaceStopOrder(aSide: TsgcHTTPBinanceOrderSide; const aSymbol: string; aQuantity, aStopPrice, aLimitPrice: Double): string;
function PlaceStopTrailingOrder(aSide: TsgcHTTPBinanceOrderSide; const aSymbol: string; aQuantity: Double; aTrailingDelta: Int64; aLimitPrice: Double): string;
function PlaceTakeProfitOrder(aSide: TsgcHTTPBinanceOrderSide; const aSymbol: string; aQuantity, aStopPrice, aLimitPrice: Double): string;
function PlaceTakeProfitTrailingOrder(aSide: TsgcHTTPBinanceOrderSide; const aSymbol: string; aQuantity: Double; aTrailingDelta: Int64; aLimitPrice: Double): string;
function PlaceLimitMakerOrder(aSide: TsgcHTTPBinanceOrderSide; const aSymbol: string; aQuantity: Double): string;
function TestNewOrder(const aSymbol, aSide, aType: String; aTimeInForce: String = ''; aQuantity: Double = 0; aQuoteOrderQty: Double = 0; aPrice: Double = 0; aNewClientOrderId: String = ''; aStopPrice: Double = 0; aIcebergQty: Double = 0; aTrailingDelta: Int64 = 0; aNewOrderRespType: String = ''; aSelfTradePreventionMode: String = ''; aStrategyId: Int64 = 0; aStrategyType: Integer = 0): String;
function QueryOrder(const aSymbol: String; aOrderId: Int64 = 0; const aOrigClientOrderId: String = ''): string;
function CancelOrder(const aSymbol: String; aOrderId: Int64 = 0; const aOrigClientOrderId: String = ''; aCancelRestrictions: String = ''): string;
function CancelReplaceOrder(const aSymbol, aSide, aType, aCancelReplaceMode : String; aTimeInForce: String = ''; aQuantity: Double = 0; aQuoteOrderQty: Double = 0; aPrice: Double = 0; aCancelNewClientOrderId: String = ''; aCancelOrigClientOrderId: String = ''; aCancelOrderId: Int64 = 0; aNewClientOrderId: String = ''; aStopPrice: Double = 0; aTrailingDelta: Int64 = 0; aIcebergQty: Double = 0; aNewOrderRespType: String = ''; aSelfTradePreventionMode: String = ''; aCancelRestrictions: String = ''; aStrategyId: Int64 = 0; aStrategyType: Integer = 0): String;
function CancelAllOpenOrders(const aSymbol: String): string;
function GetOpenOrders(const aSymbol: String = ''): string;
function GetAllOrders(const aSymbol: String; aOrderId: Int64 = 0; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 500): string;
function NewOCO(const aSymbol, aSide: String; aQuantity, aPrice, aStopPrice: Double; const aListClientOrderId: String = ''; aLimitClientOrderId: string = ''; aLimitIcebergQty: Double = 0; aStopClientOrderId: string = ''; aStopLimitPrice: Double = 0; aStopIcebergQty: Double = 0; aStopLimitTimeInForce: String = ''; aNewOrderRespType: String = ''): String;
function CancelOCO(const aSymbol: String; aOrderListId: Integer = 0; const aListClientOrderId: String = ''; aNewClientOrderId: String = ''): string;
function QueryOCO(const aSymbol: String; aOrderListId: Integer = 0; const aOrigClientOrderId: String = ''): string;
function GetAllOCO(aFromId: Integer = 0; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 500): string;
function GetOpenOCO: string;
function NewOrderListOCO(const aSymbol, aSide: String; aQuantity: Double; const aAboveType: String; const aBelowType: String; aAboveClientOrderId: String = ''; aAboveIcebergQty: Double = 0; aAbovePrice: Double = 0; aAboveStopPrice: Double = 0; aAboveTrailingDelta: Int64 = 0; aAboveTimeInForce: String = ''; aBelowClientOrderId: String = ''; aBelowIcebergQty: Double = 0; aBelowPrice: Double = 0; aBelowStopPrice: Double = 0; aBelowTrailingDelta: Int64 = 0; aBelowTimeInForce: String = ''; aListClientOrderId: String = ''; aNewOrderRespType: String = ''; aSelfTradePreventionMode: String = ''): String;
function NewOrderListOTO(const aSymbol: String; const aWorkingType, aWorkingSide: String; aWorkingQuantity: Double; aWorkingPrice: Double; const aPendingType, aPendingSide: String; aPendingQuantity: Double; aWorkingClientOrderId: String = ''; aWorkingTimeInForce: String = ''; aWorkingIcebergQty: Double = 0; aPendingClientOrderId: String = ''; aPendingPrice: Double = 0; aPendingStopPrice: Double = 0; aPendingTrailingDelta: Int64 = 0; aPendingTimeInForce: String = ''; aPendingIcebergQty: Double = 0; aListClientOrderId: String = ''; aNewOrderRespType: String = ''; aSelfTradePreventionMode: String = ''): String;
function NewOrderListOTOCO(const aSymbol: String; const aWorkingType, aWorkingSide: String; aWorkingQuantity: Double; aWorkingPrice: Double; const aPendingSide, aPendingAboveType, aPendingBelowType: String; aPendingQuantity: Double; aWorkingClientOrderId: String = ''; aWorkingTimeInForce: String = ''; aWorkingIcebergQty: Double = 0; aPendingAboveClientOrderId: String = ''; aPendingAbovePrice: Double = 0; aPendingAboveStopPrice: Double = 0; aPendingAboveTrailingDelta: Int64 = 0; aPendingAboveTimeInForce: String = ''; aPendingAboveIcebergQty: Double = 0; aPendingBelowClientOrderId: String = ''; aPendingBelowPrice: Double = 0; aPendingBelowStopPrice: Double = 0; aPendingBelowTrailingDelta: Int64 = 0; aPendingBelowTimeInForce: String = ''; aPendingBelowIcebergQty: Double = 0; aListClientOrderId: String = ''; aNewOrderRespType: String = ''; aSelfTradePreventionMode: String = ''): String;
function NewSOROrder(const aSymbol, aSide, aType: String; aQuantity: Double; aTimeInForce: String = ''; aPrice: Double = 0; aNewClientOrderId: String = ''; aNewOrderRespType: String = ''; aIcebergQty: Double = 0; aSelfTradePreventionMode: String = ''; aStrategyId: Int64 = 0; aStrategyType: Integer = 0): String;
function TestSOROrder(const aSymbol, aSide, aType: String; aQuantity: Double; aTimeInForce: String = ''; aPrice: Double = 0; aNewClientOrderId: String = ''; aNewOrderRespType: String = ''; aIcebergQty: Double = 0; aSelfTradePreventionMode: String = ''; aStrategyId: Int64 = 0; aStrategyType: Integer = 0): String;
function GetAccountInformation(aOmitZeroBalances: Boolean = False): String;
function GetAccountTradeList(const aSymbol: String; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aFromId: Integer = 0; aLimit: Integer = 500): String;
function GetOrderRateLimitUsage: String;
function GetPreventedMatches(const aSymbol: String; aPreventedMatchId: Int64 = 0; aOrderId: Int64 = 0; aFromPreventedMatchId: Int64 = 0; aLimit: Integer = 500): String;
function GetAllocations(const aSymbol: String; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aFromAllocationId: Integer = 0; aLimit: Integer = 500; aOrderId: Int64 = 0): String;
function GetAccountCommission(const aSymbol: String): String;
function GetAllConvertPairs(const aFromAsset: string; const aToAsset: string): string;
function GetConvertAssetInfo: string;
function SendConvertQuoteRequest(const aFromAsset, aToAsset: string; aFromAmount: Double = 0; aToAmount: Double = 0; const aWalletType: string = ''; const aValidTime: string = ''): String;
function AcceptConvertQuote(const aQuoteId: string): string;
function GetConvertOrderStatus(const aOrderId: string; const aQuoteId: string): string;
function PlaceConvertLimitOrder(const aBaseAsset, aQuoteAsset: string; aSide: TsgcHTTPBinanceOrderSide; aLimitPrice: Double; aBaseAmount: Double = 0; aQuoteAmount: Double = 0; aExpiredType: TsgcHTTPBinanceConvertOrderExpiredType = bcoet1D; const aWalletType: string = ''): String;
function CancelConvertLimitOrder(const aOrderId: Int64): String;
function GetConvertLimitOpenOrders: String;
function GetConvertTradeHistory(const aStartTime, aEndTime: TDateTime; aLimit: Integer = 0): string;
function GetWalletSystemStatus: String;
function GetWalletAllCoinsInformation: String;
function GetWalletDailyAccountSnapshot(const aType: string = 'SPOT'; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 7): String;
function SetWalletDisableFastWithdrawSwitch: String;
function SetWalletEnableFastWithdrawSwitch: String;
function WalletWithdraw(const aCoin, aAddress: string; aAmount: Double; aOrderId: string = ''; aNetworkd: string = ''; aAddressTag: string = ''; aTransactionFeeFlag: Boolean = False; aName: string = ''; aWalletType: Integer = 0): string;
function GetWalletDepositHistory(const aCoin: string = ''; aStatus: Integer = -1; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aOffset: Integer = 0; aLimit: Integer = 1000): String;
function GetWalletWithdrawHistory(const aCoin: string = ''; const aOrderId: string = ''; aStatus: Integer = -1; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aOffset: Integer = 0; aLimit: Integer = 1000): String;
function GetWalletDepositAddress(const aCoin: string; const aNetwork: string = ''): String;
function GetWalletAccountStatus: String;
function GetWalletAccountAPITradingStatus: string;
function GetWalletDustLog(aStartTime: Int64 = 0; aEndTime: Int64 = 0): String;
function GetWalletAssetsConvertedBNB: String;
function WalletDustTransfer(const aAsset: string): String;
function GetWalletAssetDividendRecord(const aAsset: string = ''; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 20): String;
function GetWalletAssetDetail(const aAsset: string = ''): String;
function GetWalletTradeFee(const aSymbol: string = ''): String;
function WalletUserUniversalTransfer(const aType, aAsset: string; aAmount: Double; aFromSymbol: string = ''; aToSymbol: string = ''): string;
function GetWalletQueryUserUniversalTransferHistory(const aType: string; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aCurrent: Integer = 1; aSize: Integer = 10; aFromSymbol: String = ''; aToSymbol: String = ''): String;
function GetWalletFundingWallet(const aAsset: string = ''; aNeetBTCValuation: Boolean = False): String;
function GetWalletUserAsset(const aAsset: string = ''; aNeetBTCValuation: Boolean = False): String;
function GetWalletApiKeyPermission: String;
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

