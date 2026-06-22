# TsgcWSAPI_Binance

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Binance: TsgcWSBinance_Options` | [TsgcWSBinance_Options](../types/TsgcWSBinance_Options.md) | `__property TsgcWSBinance_Options * Binance;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_Binance_Rest` | [TsgcHTTP_API_Binance_Rest](../types/TsgcHTTP_API_Binance_Rest.md) | `__property TsgcHTTP_API_Binance_Rest * REST_API;` |
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
function SubscribeTrades(const aSymbol: String): Integer;
function UnSubscribeTrades(const aSymbol: String): Integer;
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
function SubscribePartialBookDepth(const aSymbol: String; const aDepth: TsgcWSBinanceDepthLevels; aUpdateSpeed: string = ''): Integer;
function UnSubscribePartialBookDepth(const aSymbol: String; const aDepth: TsgcWSBinanceDepthLevels): Integer;
function SubscribeDiffDepth(const aSymbol: String): Integer;
function UnSubscribeDiffDepth(const aSymbol: String): Integer;
function SubscribeAvgPrice(const aSymbol: String): Integer;
function UnSubscribeAvgPrice(const aSymbol: String): Integer;
function SubscribeRollingWindowTicker(const aSymbol: String; const aWindowSize: TsgcWSBinanceRollingWindowSize): Integer;
function UnSubscribeRollingWindowTicker(const aSymbol: String; const aWindowSize: TsgcWSBinanceRollingWindowSize): Integer;
function SubscribeAllRollingWindowTickers( const aWindowSize: TsgcWSBinanceRollingWindowSize): Integer;
function UnSubscribeAllRollingWindowTickers( const aWindowSize: TsgcWSBinanceRollingWindowSize): Integer;
function ListSubscriptions: Integer;
procedure QueueClear;
```

C++Builder

```cpp
int __fastcall SubscribeAggregateTrades(const UnicodeString aSymbol);
int __fastcall UnSubscribeAggregateTrades(const UnicodeString aSymbol);
int __fastcall SubscribeTrades(const UnicodeString aSymbol);
int __fastcall UnSubscribeTrades(const UnicodeString aSymbol);
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
int __fastcall SubscribePartialBookDepth(const UnicodeString aSymbol, const TsgcWSBinanceDepthLevels * aDepth, UnicodeString aUpdateSpeed = '');
int __fastcall UnSubscribePartialBookDepth(const UnicodeString aSymbol, const TsgcWSBinanceDepthLevels * aDepth);
int __fastcall SubscribeDiffDepth(const UnicodeString aSymbol);
int __fastcall UnSubscribeDiffDepth(const UnicodeString aSymbol);
int __fastcall SubscribeAvgPrice(const UnicodeString aSymbol);
int __fastcall UnSubscribeAvgPrice(const UnicodeString aSymbol);
int __fastcall SubscribeRollingWindowTicker(const UnicodeString aSymbol, const TsgcWSBinanceRollingWindowSize * aWindowSize);
int __fastcall UnSubscribeRollingWindowTicker(const UnicodeString aSymbol, const TsgcWSBinanceRollingWindowSize * aWindowSize);
int __fastcall SubscribeAllRollingWindowTickers(const TsgcWSBinanceRollingWindowSize * aWindowSize);
int __fastcall UnSubscribeAllRollingWindowTickers(const TsgcWSBinanceRollingWindowSize * aWindowSize);
int __fastcall ListSubscriptions();
void __fastcall QueueClear();
```

