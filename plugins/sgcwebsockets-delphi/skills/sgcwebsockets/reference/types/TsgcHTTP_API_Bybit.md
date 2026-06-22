# TsgcHTTP_API_Bybit

kind: class
unit: sgcHTTP_API_Bybit

## Properties

| Delphi | Type |
| --- | --- |
| `BybitClient: TsgcWSBybitClient` | [TsgcWSBybitClient](./TsgcWSBybitClient.md) |
| `BybitOptions: TsgcHTTPBybit_Options` | [TsgcHTTPBybit_Options](./TsgcHTTPBybit_Options.md) |
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
function GetServerTime: string;
function GetKLine(const aSymbol: string; aInterval: TsgcBybitKLineInterval; aStart: Int64 = 0; aEnd: Int64 = 0; aLimit: Integer = 200): string;
function GetMarkPriceKLine(const aSymbol: string; aInterval: TsgcBybitKLineInterval; aStart: Int64 = 0; aEnd: Int64 = 0; aLimit: Integer = 200): string;
function GetIndexPriceKLine(const aSymbol: string; aInterval: TsgcBybitKLineInterval; aStart: Int64 = 0; aEnd: Int64 = 0; aLimit: Integer = 200): string;
function GetPremiumIndexPriceKLine(const aSymbol: string; aInterval: TsgcBybitKLineInterval; aStart: Int64 = 0; aEnd: Int64 = 0; aLimit: Integer = 200): string;
function GetInstrumentsInfo(const aSymbol: string = ''; const aStatus: string = ''; const aBaseCoin: string = ''; aLimit: Integer = 500; const aCursor: string = ''): string;
function GetOrderBook(const aSymbol: string; aLimit: Integer = 0): string;
function GetTickers(const aSymbol: string = ''; const aBaseCoin: string = ''; const aExpDate: String = ''): string;
function GetFundingRateHistory(const aSymbol: string; aStart: Int64 = 0; aEnd: Int64 = 0; aLimit: Integer = 200): string;
function GetPublicRecentTradingHistory(const aSymbol: string = ''; const aBaseCoin: string = ''; const aOptionType: string = ''; aLimit: Integer = 0): string;
function GetOpenInterest(const aSymbol: string; aIntervalTime: TsgcBybitKLineInterval; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 50; const aCursor: string = ''): string;
function GetHistoricalVolatility(const aBaseCoin: string = ''; const aPeriod: Integer = 0; aStartTime: Int64 = 0; aEndTime: Int64 = 0): string;
function GetInsurance(const aCoin: string = ''): string;
function GetRiskLimit(const aSymbol: string = ''): string;
function GetDeliveryPrice(const aSymbol: string = ''; const aBaseCoin: string = ''; aLimit: Integer = 50; const aCursor: string = ''): string;
function GetLongShortRatio(const aSymbol: string; aPeriod: TsgcBybitKLineInterval; aLimit: Integer = 50): string;
function PlaceOrder(const aOrder: TsgcBybitOrder): string;
function PlaceMarketOrder(const aSymbol: string; aSide: TsgcHTTPBybitOrderSide; aQty: string; aReduceOnly: Boolean = false; aStopLoss: string = ''; aTakeProfit: string = ''): string;
function PlaceLimitOrder(const aSymbol: string; aSide: TsgcHTTPBybitOrderSide; aQty, aPrice: string): string;
function AmendOrder(const aOrder: TsgcBybitOrder): string;
function CancelOrder(const aSymbol: string; aOrderId: string = ''; aOrderLinkId: string = ''; aOrderFilter: string = ''): string;
function GetOpenOrders(const aSymbol: string = ''; const aBaseCoin: string = ''; const aSettleCoin: string = ''; const aOrderId: string = ''; const aOrderLinkId: string = ''; aOpenOnly: Integer = 0; const aOrderFilter: string = ''; aLimit: Integer = 20; const aCursor: string = ''): string;
function CancelAllOrders(const aSymbol: string = ''; const aBaseCoin: string = ''; const aSettleCoin: string = ''; const aOrderFilter: string = ''; const aStopOrderType: string = ''): string;
function GetOrderHistory(const aSymbol: string = ''; const aBaseCoin: string = ''; const aSettleCoin: string = ''; const aOrderId: string = ''; const aOrderLinkId: string = ''; const aOrderFilter: string = ''; const aOrderStatus: string = ''; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 20; const aCursor: string = ''): string;
function BatchPlaceOrder(const aOrders: string): string;
function BatchAmendOrder(const aOrders: string): string;
function BatchCancelOrder(const aOrders: string): string;
function SetDCP(aDcpTimeInMs: Integer): string;
function GetPositionInfo(const aSymbol: string = ''; const aStatus: string = ''; const aBaseCoin: string = ''; const aSettleCoin: string = ''; aLimit: Integer = 20; const aCursor: string = ''): string;
function SetLeverage(const aSymbol: string; const aBuyLeverage: string; const aSellLeverage: string): string;
function SwitchCrossIsolatedMargin(const aSymbol: string; aTradeMode: Integer; const aBuyLeverage, aSellLeverage: string): string;
function SetTPSLMode(const aSymbol, aTPSLMode: string): string;
function SwitchPositionMode(aMode: Integer; const aSymbol: string = ''; const aCoin: string = ''): string;
function SetRiskLimit(const aSymbol: string; const aRiskId: Integer; aPositionIdx: Integer = -1): string;
function SetTradingStop(const aStop: TsgcBybitStopOrder): string;
function SetAutoAddMargin(const aSymbol: string; const aAutoAddMargin: Integer; aPositionIdx: Integer = -1): string;
function AddOrReduceMargin(const aSymbol, aMargin: string; aPositionIdx: Integer = -1): string;
function GetExecution(const aSymbol: string = ''; const aOrderId: string = ''; const aOrderLinkId: string = ''; const aBaseCoin: string = ''; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aExecType: string = ''; aLimit: Integer = 50; const aCursor: string = ''): string;
function GetClosedPNL(const aSymbol: string = ''; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 50; const aCursor: string = ''): string;
function ConfirmNewRiskLimit(const aSymbol: string): string;
function GetWalletBalance(const aCategory: string; const aCoin: string = ''): string;
function GetAccountInfo: string;
function GetTransactionLog(const aAccountType: string = ''; const aCategory: string = ''; const aCurrency: string = ''; const aBaseCoin: string = ''; const aType: string = ''; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 50; const aCursor: string = ''): string;
function GetFeeRate(const aSymbol: string = ''): string;
function GetCollateralInfo(const aCurrency: string = ''): string;
function SetMarginMode(const aSetMarginMode: string): string;
function GetBorrowHistory(const aCurrency: string = ''; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 50; const aCursor: string = ''): string;
function GetCoinGreeks(const aBaseCoin: string = ''): string;
function GetCoinInfo(const aCoin: string = ''): string;
function GetAllCoinsBalance(const aAccountType: string; const aCoin: string = ''): string;
function CreateInternalTransfer(const aTransferId, aCoin: string; aAmount: Double; const aFromAccountType, aToAccountType: string): string;
function GetInternalTransferList(const aTransferId: string = ''; const aCoin: string = ''; const aStatus: string = ''; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 50; const aCursor: string = ''): string;
function GetDepositRecords(const aCoin: string = ''; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 50; const aCursor: string = ''): string;
function GetDepositAddress(const aCoin: string; const aChainType: string = ''): string;
function CreateWithdrawal(const aCoin, aChain, aAddress: string; aAmount: Double; const aTag: string = ''; aForceChain: Integer = 0; const aAccountType: string = ''): string;
function CancelWithdrawal(const aId: string): string;
function GetWithdrawalRecords(const aCoin: string = ''; const aWithdrawType: string = ''; aStartTime: Int64 = 0; aEndTime: Int64 = 0; aLimit: Integer = 50; const aCursor: string = ''): string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

