# TsgcHTTP_API_Coinbase_Rest

kind: class
unit: sgcHTTP_API_Coinbase

## Properties

| Delphi | Type |
| --- | --- |
| `CoinbaseOptions: TsgcHTTPCoinbase_Options` | [TsgcHTTPCoinbase_Options](./TsgcHTTPCoinbase_Options.md) |
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
function ListAccounts: string;
function GetAccount(const aAccountId: string): string;
function PlaceNewOrder(const aOrder: TsgcHTTPCoinbaseOrder): string;
function PlaceMarketOrder(const aSide: TsgcHTTPCoinbaseOrderSide; const aProductId: string; const aQuoteSize, aBaseSize: Extended; aClient_oid: string = ''): string;
function PlaceLimitOrder(const aSide: TsgcHTTPCoinbaseOrderSide; const aProductId: string; aQuoteSize, aBaseSize, aLimitPrice: Extended; aClient_oid: string = ''): string;
function PlaceStopOrder(const aSide: TsgcHTTPCoinbaseOrderSide; const aProductId: string; aBaseSize, aStopPrice, aLimitPrice: Extended; aStopDirection: TsgcHTTPCoinbaseOrderStopDirection; aClient_oid: string = ''): string;
function CancelOrder(const aOrderId: string): string;
function EditOrder(const aOrderId: string; aPrice, aSize: Extended): string;
function EditOrderPreview(const aOrderId: string; aPrice, aSize: Extended): string;
function ListOrders(const aOrderId: string = ''; const aProductId: String = ''; const aOrderStatus: string = ''): string;
function GetOrder(const aOrderId: string): string;
function PreviewOrder(const aOrder: TsgcHTTPCoinbaseOrder): string;
function ClosePosition(const aOrderId, aProductId: string; aSize: Extended = 0): string;
function GetFillsByOrderId(const aOrderId: string): string;
function GetFillsByProductId(const aProductId: string): string;
function GetFillsByTradeId(const aTradeId: string): string;
function CreateConvertQuote(const aFromAccount, aToAccount: string; aAmount: Extended): string;
function CommitConvertTrade(const aTradeId, aFromAccount, aToAccount: string): string;
function GetConvertTrade(const aTradeId, aFromAccount, aToAccount: string): string;
function GetTransactionSummary(const aProductType: string = ''; const aContractExpiryType: string = ''): string;
function ListProducts(const aProductType: string = ''; const aProductIds: string = ''): string;
function GetProduct(const aProductId: string): string;
function GetProductBook(const aProductId: string; aLimit: Integer = 0): string;
function GetProductCandles(const aProductId: string; const aStart, aEnd: string; aGranularity: string): string;
function GetMarketTrades(const aProductId: string; aLimit: Integer = 100): string;
function GetBestBidAsk(const aProductIds: string = ''): string;
function ListPortfolios: string;
function CreatePortfolio(const aName: string): string;
function DeletePortfolio(const aPortfolioId: string): string;
function GetPortfolioBreakdown(const aPortfolioId: string): string;
function MovePortfolioFunds(const aValue, aCurrency, aSourcePortfolio, aTargetPortfolio: string): string;
function GetPerpetualsPortfolioSummary( const aPortfolioUuid: string): string;
function ListPerpetualsPositions( const aPortfolioUuid: string): string;
function GetPerpetualsPosition(const aPortfolioUuid, aSymbol: string): string;
function GetTime: string;
function Get(const aURL: String; const aHeaders: TStrings = nil; aSSE: Boolean = False): String;
function Post(const aURL, aBody: String; const aHeaders: TStrings = nil; const aMultipartFormData: TIdMultiPartFormDataStream = nil; aForceHTTP1: Boolean = False; aSSE: Boolean = False; const aResponseHeaders: TStrings = nil): String;
function Delete(const aURL: String; const aHeader: TStrings = nil; const aBody: string = ''): String;
function Patch(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
function Put(const aURL, aBody: String; const aHeaders: TStrings = nil): String;
```

