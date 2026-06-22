# TsgcHTTP_API_Kucoin_Rest

kind: class
unit: sgcHTTP_API_Kucoin

## Properties

| Delphi | Type |
| --- | --- |
| `KucoinOptions: TsgcHTTPKucoin_Options` | [TsgcHTTPKucoin_Options](./TsgcHTTPKucoin_Options.md) |
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
function GetAllSubAccounts: string;
function GetListAccounts: string;
function GetAccount(const aAccountId: string): string;
function GetAccountBalanceSubAccount(const aSubUserId: string): string;
function InnerTransfer(const aClientOid, aCurrency: string; aFrom: TsgcHTTPKucoinTransferFrom; aTo: TsgcHTTPKucoinTransferTo; aAmount: Double; const aFromTag: string = ''; const aToTag: string = ''): string;
function GetWithdrawalsList(const aCurrency: string = ''; const aStatus: string = ''; aStartAt: Int64 = 0; aEndAt: Int64 = 0): string;
function GetHistoricalWithdrawalsList(aCurrentPage: Integer = 0; aPageSize: Integer = 0; const aCurrency: string = ''; aStartAt: Int64 = 0; aEndAt: Int64 = 0; const aStatus: string = ''): string;
function GetWithdrawalsQuotas(const aCurrency: string; const aChain: string = ''): string;
function ApplyWithdraw(const aCurrency, aAddress: string; aAmount: Double; const aMemo: string = ''; aIsInner: Boolean = False; const aRemark: string = ''; const aChain: string = ''; const aFeeDeductType: string = ''): string;
function CancelWithdraw(const aWithdrawalId: string): string;
function GetDepositAddresses(const aCurrency: string; const aChain: string = ''): string;
function CreateDepositAddress(const aCurrency: string; const aChain: string = ''): string;
function GetDepositList(const aCurrency: string = ''; const aStatus: string = ''; aStartAt: Int64 = 0; aEndAt: Int64 = 0): string;
function GetAccountLedgers(const aCurrency: string = ''; const aDirection: string = ''; const aBizType: string = ''; aStartAt: Int64 = 0; aEndAt: Int64 = 0): string;
function GetTradeFees(const aSymbols: string): string;
function PlaceOrder(const aOrder: TsgcHTTPKucoinSpotOrder): string;
function PlaceMarketOrder(aSide: TsgcHTTPKucoinOrderSide; const aSymbol: string; aSize: Extended; const aClientOid: string = ''; aFunds: Extended = 0): string;
function PlaceLimitOrder(aSide: TsgcHTTPKucoinOrderSide; const aSymbol: string; aSize, aPrice: Extended; const aClientOid: string = ''): string;
function PlaceMarginOrder(const aOrder: TsgcHTTPKucoinSpotOrder): string;
function CancelOrder(const aOrderId: string): string;
function CancelOrderByClientOid(const aClientOid: string): string;
function CancelAllOrders(const aSymbol: string = ''; aTradeType: TsgcHTTPKucoinTradeType = kttNone): string;
function ListOrders(const aStatus: string = ''; const aSymbol: string = ''; aSide: TsgcHTTPKucoinOrderSide = kosNone; aOrderType: TsgcHTTPKucoinOrderType = kotNone; aTradeType: TsgcHTTPKucoinTradeType = kttNone; aStartAt: Int64 = 0; aEndAt: Int64 = 0): string;
function GetRecentOrders: string;
function GetOrder(const aOrderId: string): string;
function GetOrderByClientOid(const aClientOid: string): string;
function ListFills(const aOrderId: string = ''; const aSymbol: string = ''; aSide: TsgcHTTPKucoinOrderSide = kosNone; aOrderType: TsgcHTTPKucoinOrderType = kotNone; aStartAt: Int64 = 0; aEndAt: Int64 = 0; aTradeType: TsgcHTTPKucoinTradeType = kttNone): string;
function GetRecentFills: string;
function PlaceStopOrder(const aOrder: TsgcHTTPKucoinSpotOrder): string;
function PlaceStopMarketOrder(aSide: TsgcHTTPKucoinOrderSide; const aSymbol: string; aSize, aStopPrice: Extended; aStop: TsgcHTTPKucoinStopType = kstNone; aFunds: Extended = 0; const aClientOid: string = ''): string;
function PlaceStopLimitOrder(aSide: TsgcHTTPKucoinOrderSide; const aSymbol: string; aSize, aPrice: Extended; aStopPrice: Extended; aStop: TsgcHTTPKucoinStopType = kstNone; const aClientOid: string = ''): string;
function CancelStopOrder(const aOrderId: string): string;
function CancelStopOrderByClientOid(const aClientOid: string; const aSymbol: string = ''): string;
function CancelAllStopOrders(const aSymbol: string = ''; aTradeType: TsgcHTTPKucoinTradeType = kttNone; aOrderIds: string = ''): string;
function GetStopOrder(const aOrderId: string): string;
function GetStopOrderByClientOid(const aClientOid: string): string;
function ListStopOrders(const aSymbol: string = ''; aSide: TsgcHTTPKucoinOrderSide = kosNone; aOrderType: TsgcHTTPKucoinOrderType = kotNone; aTradeType: TsgcHTTPKucoinTradeType = kttNone; aStartAt: Int64 = 0; aEndAt: Int64 = 0; aCurrentPage: Integer = 0; aOrderIds: string = ''; aPageSize: Integer = 0): string;
function GetSymbolList(const aMarket: string): string;
function GetTicker(const aSymbol: string): string;
function GetAllTickers: string;
function Get24hrStats(const aSymbol: string): string;
function GetMarketList: string;
function GetPartOrderBook1(const aSymbol: string): string;
function GetPartOrderBook20(const aSymbol: string): string;
function GetPartOrderBook100(const aSymbol: string): string;
function GetFullOrderBook(const aSymbol: string): string;
function GetHistories(const aSymbol: string): string;
function GetKLines(const aSymbol: string; const aInterval: TsgcHTTPKucoinChartIntervals; aStartAt: Int64 = 0; aEndAt: Int64 = 0): string;
function GetCurrencies: string;
function GetCurrencyDetail(const aCurrency: string; const aChain: string = ''): string;
function GetFiatPrice(const aBase: string = ''; const aCurrencies: string = ''): string;
function PlaceHFOrder(const aOrder: TsgcHTTPKucoinSpotOrder): string;
function CancelHFOrder(const aOrderId: string; const aSymbol: string): string;
function CancelHFOrderByClientOid(const aClientOid: string; const aSymbol: string): string;
function CancelAllHFOrders(const aSymbol: string = ''): string;
function GetHFActiveOrders(const aSymbol: string): string;
function GetHFDoneOrders(const aSymbol: string; aSide: TsgcHTTPKucoinOrderSide = kosNone; aOrderType: TsgcHTTPKucoinOrderType = kotNone; aStartAt: Int64 = 0; aEndAt: Int64 = 0; aLastId: Int64 = 0; aLimit: Integer = 20): string;
function GetHFOrder(const aOrderId: string; const aSymbol: string): string;
function GetServerTime: String;
function GetServiceStatus: String;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

