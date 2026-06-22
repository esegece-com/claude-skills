# TsgcWSAPI_Kucoin

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Kucoin: TsgcWSKucoin_Options` | [TsgcWSKucoin_Options](../types/TsgcWSKucoin_Options.md) | `__property TsgcWSKucoin_Options * Kucoin;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_Kucoin_Rest` | [TsgcHTTP_API_Kucoin_Rest](../types/TsgcHTTP_API_Kucoin_Rest.md) | `__property TsgcHTTP_API_Kucoin_Rest * REST_API;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnKucoinHTTPException: TsgcWSKucoinHTTPExceptionEvent` | [TsgcWSKucoinHTTPExceptionEvent](../types/TsgcWSKucoinHTTPExceptionEvent.md) | `__property TsgcWSKucoinHTTPExceptionEvent OnKucoinHTTPException;` |
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
function SubscribeSymbolTicker(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeSymbolTicker(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeAllSymbolsTicker(aAck: Boolean = False): Integer;
function UnSubscribeAllSymbolsTicker(aAck: Boolean = False): Integer;
function SubscribeSymbolSnapshot(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeSymbolSnapshot(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeMarketSnapshot(const aMarket: string; aAck: Boolean = False): Integer;
function UnSubscribeMarketSnapshot(const aMarket: string; aAck: Boolean = False): Integer;
function SubscribeLevel2MarketData(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeLevel2MarketData(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeLevel2_5BestAskBid(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeLevel2_5BestAskBid(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeLevel2_50BestAskBid(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeLevel2_50BestAskBid(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeKlines(const aSymbol: string; aKlines: TsgcWSKucoinKlines; aAck: Boolean = False): Integer;
function UnSubscribeKlines(const aSymbol: string; aKlines: TsgcWSKucoinKlines; aAck: Boolean = False): Integer;
function SubscribeMatchExecutionData(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeMatchExecutionData(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeIndexPrice(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeIndexPrice(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeMarkPrice(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeMarkPrice(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeOrderBookChanged(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeOrderBookChanged(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeLevel1(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeLevel1(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeTradeOrders(aAck: Boolean = False): Integer;
function UnSubscribeTradeOrders(aAck: Boolean = False): Integer;
function SubscribeAccountBalance(aAck: Boolean = False): Integer;
function UnSubscribeAccountBalance(aAck: Boolean = False): Integer;
function SubscribePositionStatus(aAck: Boolean = False): Integer;
function UnSubscribePositionStatus(aAck: Boolean = False): Integer;
function SubscribeMarginTradeOrders(const aCurrency: string; aAck: Boolean = False): Integer;
function UnSubscribeMarginTradeOrders(const aCurrency: string; aAck: Boolean = False): Integer;
function SubscribeStopOrder(aAck: Boolean = False): Integer;
function UnSubscribeStopOrder(aAck: Boolean = False): Integer;
function SubscribeTradeOrdersV2(aAck: Boolean = False): Integer;
function UnSubscribeTradeOrdersV2(aAck: Boolean = False): Integer;
function SubscribeCrossMarginPosition(aAck: Boolean = False): Integer;
function UnSubscribeCrossMarginPosition(aAck: Boolean = False): Integer;
function SubscribeIsolatedMarginPosition(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeIsolatedMarginPosition(const aSymbol: string; aAck: Boolean = False): Integer;
procedure QueueClear;
```

C++Builder

```cpp
int __fastcall SubscribeSymbolTicker(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeSymbolTicker(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeAllSymbolsTicker(bool aAck = False);
int __fastcall UnSubscribeAllSymbolsTicker(bool aAck = False);
int __fastcall SubscribeSymbolSnapshot(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeSymbolSnapshot(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeMarketSnapshot(const UnicodeString aMarket, bool aAck = False);
int __fastcall UnSubscribeMarketSnapshot(const UnicodeString aMarket, bool aAck = False);
int __fastcall SubscribeLevel2MarketData(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeLevel2MarketData(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeLevel2_5BestAskBid(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeLevel2_5BestAskBid(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeLevel2_50BestAskBid(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeLevel2_50BestAskBid(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeKlines(const UnicodeString aSymbol, TsgcWSKucoinKlines * aKlines, bool aAck = False);
int __fastcall UnSubscribeKlines(const UnicodeString aSymbol, TsgcWSKucoinKlines * aKlines, bool aAck = False);
int __fastcall SubscribeMatchExecutionData(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeMatchExecutionData(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeIndexPrice(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeIndexPrice(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeMarkPrice(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeMarkPrice(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeOrderBookChanged(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeOrderBookChanged(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeLevel1(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeLevel1(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeTradeOrders(bool aAck = False);
int __fastcall UnSubscribeTradeOrders(bool aAck = False);
int __fastcall SubscribeAccountBalance(bool aAck = False);
int __fastcall UnSubscribeAccountBalance(bool aAck = False);
int __fastcall SubscribePositionStatus(bool aAck = False);
int __fastcall UnSubscribePositionStatus(bool aAck = False);
int __fastcall SubscribeMarginTradeOrders(const UnicodeString aCurrency, bool aAck = False);
int __fastcall UnSubscribeMarginTradeOrders(const UnicodeString aCurrency, bool aAck = False);
int __fastcall SubscribeStopOrder(bool aAck = False);
int __fastcall UnSubscribeStopOrder(bool aAck = False);
int __fastcall SubscribeTradeOrdersV2(bool aAck = False);
int __fastcall UnSubscribeTradeOrdersV2(bool aAck = False);
int __fastcall SubscribeCrossMarginPosition(bool aAck = False);
int __fastcall UnSubscribeCrossMarginPosition(bool aAck = False);
int __fastcall SubscribeIsolatedMarginPosition(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeIsolatedMarginPosition(const UnicodeString aSymbol, bool aAck = False);
void __fastcall QueueClear();
```

