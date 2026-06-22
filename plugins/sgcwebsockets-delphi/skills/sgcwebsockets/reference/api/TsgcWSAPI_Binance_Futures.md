# TsgcWSAPI_Binance_Futures

unit: sgcWebSocket_APIs
Edition: Standard

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Binance: TsgcWSBinance_Options` | [TsgcWSBinance_Options](../types/TsgcWSBinance_Options.md) | `__property TsgcWSBinance_Options * Binance;` |
| `FuturesContracts: TsgcWSBinanceFuturesContracts` | [TsgcWSBinanceFuturesContracts](../types/TsgcWSBinanceFuturesContracts.md) | `__property TsgcWSBinanceFuturesContracts * FuturesContracts;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_Binance_Futures_Rest` | [TsgcHTTP_API_Binance_Futures_Rest](../types/TsgcHTTP_API_Binance_Futures_Rest.md) | `__property TsgcHTTP_API_Binance_Futures_Rest * REST_API;` |
| `ListenKey: string (read-only)` | `string` | `__property UnicodeString ListenKey /* read-only */;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnBinanceHTTPException: TsgcWSBinanceHTTPExceptionEvent` | [TsgcWSBinanceHTTPExceptionEvent](../types/TsgcWSBinanceHTTPExceptionEvent.md) | `__property TsgcWSBinanceHTTPExceptionEvent OnBinanceHTTPException;` |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
function SubscribeAggregateTrades(const aSymbol: String): Integer;
function UnSubscribeAggregateTrades(const aSymbol: String): Integer;
function SubscribeMarkPrice(const aSymbol: String; const aUpdateSpeed: String = '@1s'): Integer;
function UnSubscribeMarkPrice(const aSymbol: String): Integer;
function SubscribeMarkPriceAllMarket(const aSymbol: String; const aUpdateSpeed: String = '@1s'): Integer;
function UnSubscribeMarkPriceAllMarket(const aSymbol: String): Integer;
function SubscribeKLine(const aSymbol: String; const aInterval: TsgcWSBinanceChartIntervals): Integer;
function UnSubscribeKLine(const aSymbol: String; const aInterval: TsgcWSBinanceChartIntervals): Integer;
function SubscribeMiniTicker(const aSymbol: String): Integer;
function UnSubscribeMiniTicker(const aSymbol: String): Integer;
function SubscribeAllMiniTickers: Integer;
function UnSubscribeAllMiniTickers: Integer;
function SubscribeTicker(const aSymbol: String): Integer;
function UnSubscribeTicker(const aSymbol: String): Integer;
function SubscribeAllMarketTickers: Integer;
function UnSubscribeAllMarketTickers: Integer;
function SubscribeBookTicker(const aSymbol: String): Integer;
function UnSubscribeBookTicker(const aSymbol: String): Integer;
function SubscribeAllBookTickers: Integer;
function UnSubscribeAllBookTickers: Integer;
function SubscribeLiquidationOrders(const aSymbol: String): Integer;
function UnSubscribeLiquidationOrders(const aSymbol: String): Integer;
function SubscribeAllMarketLiquidationOrders: Integer;
function UnSubscribeAllMarketLiquidationOrders: Integer;
function SubscribePartialBookDepth(const aSymbol: String; const aDepth: TsgcWSBinanceDepthLevels; const aUpdateSpeed: string = ''): Integer;
function UnSubscribePartialBookDepth(const aSymbol: String; const aDepth: TsgcWSBinanceDepthLevels): Integer;
function SubscribeDiffDepth(const aSymbol: String; const aUpdateSpeed: string = ''): Integer;
function UnSubscribeDiffDepth(const aSymbol: String): Integer;
function SubscribeContinuousKLine(const aPair: String; const aContractType: String; const aInterval: TsgcWSBinanceChartIntervals): Integer;
function UnSubscribeContinuousKLine(const aPair: String; const aContractType: String; const aInterval: TsgcWSBinanceChartIntervals): Integer;
function SubscribeCompositeIndex(const aSymbol: String): Integer;
function UnSubscribeCompositeIndex(const aSymbol: String): Integer;
function SubscribeContractInfo: Integer;
function UnSubscribeContractInfo: Integer;
function SubscribeAssetIndex(const aSymbol: String): Integer;
function UnSubscribeAssetIndex(const aSymbol: String): Integer;
function SubscribeAllAssetIndex: Integer;
function UnSubscribeAllAssetIndex: Integer;
function SubscribeIndexPrice(const aPair: String; const aUpdateSpeed: String = ''): Integer;
function UnSubscribeIndexPrice(const aPair: String): Integer;
function SubscribeIndexPriceKLine(const aPair: String; const aInterval: TsgcWSBinanceChartIntervals): Integer;
function UnSubscribeIndexPriceKLine(const aPair: String; const aInterval: TsgcWSBinanceChartIntervals): Integer;
function SubscribeMarkPriceKLine(const aSymbol: String; const aInterval: TsgcWSBinanceChartIntervals): Integer;
function UnSubscribeMarkPriceKLine(const aSymbol: String; const aInterval: TsgcWSBinanceChartIntervals): Integer;
procedure QueueClear;
```

C++Builder

```cpp
int __fastcall SubscribeAggregateTrades(const UnicodeString aSymbol);
int __fastcall UnSubscribeAggregateTrades(const UnicodeString aSymbol);
int __fastcall SubscribeMarkPrice(const UnicodeString aSymbol, const UnicodeString aUpdateSpeed = '@1s');
int __fastcall UnSubscribeMarkPrice(const UnicodeString aSymbol);
int __fastcall SubscribeMarkPriceAllMarket(const UnicodeString aSymbol, const UnicodeString aUpdateSpeed = '@1s');
int __fastcall UnSubscribeMarkPriceAllMarket(const UnicodeString aSymbol);
int __fastcall SubscribeKLine(const UnicodeString aSymbol, const TsgcWSBinanceChartIntervals * aInterval);
int __fastcall UnSubscribeKLine(const UnicodeString aSymbol, const TsgcWSBinanceChartIntervals * aInterval);
int __fastcall SubscribeMiniTicker(const UnicodeString aSymbol);
int __fastcall UnSubscribeMiniTicker(const UnicodeString aSymbol);
int __fastcall SubscribeAllMiniTickers();
int __fastcall UnSubscribeAllMiniTickers();
int __fastcall SubscribeTicker(const UnicodeString aSymbol);
int __fastcall UnSubscribeTicker(const UnicodeString aSymbol);
int __fastcall SubscribeAllMarketTickers();
int __fastcall UnSubscribeAllMarketTickers();
int __fastcall SubscribeBookTicker(const UnicodeString aSymbol);
int __fastcall UnSubscribeBookTicker(const UnicodeString aSymbol);
int __fastcall SubscribeAllBookTickers();
int __fastcall UnSubscribeAllBookTickers();
int __fastcall SubscribeLiquidationOrders(const UnicodeString aSymbol);
int __fastcall UnSubscribeLiquidationOrders(const UnicodeString aSymbol);
int __fastcall SubscribeAllMarketLiquidationOrders();
int __fastcall UnSubscribeAllMarketLiquidationOrders();
int __fastcall SubscribePartialBookDepth(const UnicodeString aSymbol, const TsgcWSBinanceDepthLevels * aDepth, const UnicodeString aUpdateSpeed = '');
int __fastcall UnSubscribePartialBookDepth(const UnicodeString aSymbol, const TsgcWSBinanceDepthLevels * aDepth);
int __fastcall SubscribeDiffDepth(const UnicodeString aSymbol, const UnicodeString aUpdateSpeed = '');
int __fastcall UnSubscribeDiffDepth(const UnicodeString aSymbol);
int __fastcall SubscribeContinuousKLine(const UnicodeString aPair, const UnicodeString aContractType, const TsgcWSBinanceChartIntervals * aInterval);
int __fastcall UnSubscribeContinuousKLine(const UnicodeString aPair, const UnicodeString aContractType, const TsgcWSBinanceChartIntervals * aInterval);
int __fastcall SubscribeCompositeIndex(const UnicodeString aSymbol);
int __fastcall UnSubscribeCompositeIndex(const UnicodeString aSymbol);
int __fastcall SubscribeContractInfo();
int __fastcall UnSubscribeContractInfo();
int __fastcall SubscribeAssetIndex(const UnicodeString aSymbol);
int __fastcall UnSubscribeAssetIndex(const UnicodeString aSymbol);
int __fastcall SubscribeAllAssetIndex();
int __fastcall UnSubscribeAllAssetIndex();
int __fastcall SubscribeIndexPrice(const UnicodeString aPair, const UnicodeString aUpdateSpeed = '');
int __fastcall UnSubscribeIndexPrice(const UnicodeString aPair);
int __fastcall SubscribeIndexPriceKLine(const UnicodeString aPair, const TsgcWSBinanceChartIntervals * aInterval);
int __fastcall UnSubscribeIndexPriceKLine(const UnicodeString aPair, const TsgcWSBinanceChartIntervals * aInterval);
int __fastcall SubscribeMarkPriceKLine(const UnicodeString aSymbol, const TsgcWSBinanceChartIntervals * aInterval);
int __fastcall UnSubscribeMarkPriceKLine(const UnicodeString aSymbol, const TsgcWSBinanceChartIntervals * aInterval);
void __fastcall QueueClear();
```

