# TsgcWSAPI_Kucoin_Futures

unit: sgcWebSocket_APIs
Edition: Standard

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Kucoin: TsgcWSKucoin_Options` | [TsgcWSKucoin_Options](../types/TsgcWSKucoin_Options.md) | `__property TsgcWSKucoin_Options * Kucoin;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_Kucoin_Futures_Rest` | [TsgcHTTP_API_Kucoin_Futures_Rest](../types/TsgcHTTP_API_Kucoin_Futures_Rest.md) | `__property TsgcHTTP_API_Kucoin_Futures_Rest * REST_API;` |
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
function SubscribeSymbolTickerV2(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeSymbolTickerV2(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeSymbolTicker(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeSymbolTicker(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeLevel2MarketData(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeLevel2MarketData(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeExecutionData(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeExecutionData(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeLevel2_5BestAskBid(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeLevel2_5BestAskBid(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeLevel2_50BestAskBid(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeLevel2_50BestAskBid(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeContractMarketData(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeContractMarketData(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeSystemAnnouncements(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeSystemAnnouncements(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeTransactionStatistics(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeTransactionStatistics(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeKlines(const aSymbol: string; aKlines: TsgcWSKucoinKlines; aAck: Boolean = False): Integer;
function UnSubscribeKlines(const aSymbol: string; aKlines: TsgcWSKucoinKlines; aAck: Boolean = False): Integer;
function SubscribeFundingFeeSettlement(const aSymbol: string; aAck: Boolean = False): Integer;
function UnSubscribeFundingFeeSettlement(const aSymbol: string; aAck: Boolean = False): Integer;
function SubscribeTradeOrders(const aAck: Boolean = False): Integer;
function UnSubscribeTradeOrders(const aAck: Boolean = False): Integer;
function SubscribeStopOrder(const aAck: Boolean = False): Integer;
function UnSubscribeStopOrder(const aAck: Boolean = False): Integer;
function SubscribeAccountBalance(const aAck: Boolean = False): Integer;
function UnSubscribeAccountBalance(const aAck: Boolean = False): Integer;
function SubscribePositionChange(const aSymbol: string; const aAck: Boolean = False): Integer;
function UnSubscribePositionChange(const aSymbol: string; const aAck: Boolean = False): Integer;
function SubscribeMarginMode(const aAck: Boolean = False): Integer;
function UnSubscribeMarginMode(const aAck: Boolean = False): Integer;
function SubscribeCrossMarginLeverage(const aAck: Boolean = False): Integer;
function UnSubscribeCrossMarginLeverage(const aAck: Boolean = False) : Integer;
procedure QueueClear;
```

C++Builder

```cpp
int __fastcall SubscribeSymbolTickerV2(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeSymbolTickerV2(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeSymbolTicker(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeSymbolTicker(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeLevel2MarketData(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeLevel2MarketData(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeExecutionData(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeExecutionData(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeLevel2_5BestAskBid(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeLevel2_5BestAskBid(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeLevel2_50BestAskBid(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeLevel2_50BestAskBid(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeContractMarketData(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeContractMarketData(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeSystemAnnouncements(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeSystemAnnouncements(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeTransactionStatistics(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeTransactionStatistics(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeKlines(const UnicodeString aSymbol, TsgcWSKucoinKlines * aKlines, bool aAck = False);
int __fastcall UnSubscribeKlines(const UnicodeString aSymbol, TsgcWSKucoinKlines * aKlines, bool aAck = False);
int __fastcall SubscribeFundingFeeSettlement(const UnicodeString aSymbol, bool aAck = False);
int __fastcall UnSubscribeFundingFeeSettlement(const UnicodeString aSymbol, bool aAck = False);
int __fastcall SubscribeTradeOrders(const bool aAck = False);
int __fastcall UnSubscribeTradeOrders(const bool aAck = False);
int __fastcall SubscribeStopOrder(const bool aAck = False);
int __fastcall UnSubscribeStopOrder(const bool aAck = False);
int __fastcall SubscribeAccountBalance(const bool aAck = False);
int __fastcall UnSubscribeAccountBalance(const bool aAck = False);
int __fastcall SubscribePositionChange(const UnicodeString aSymbol, const bool aAck = False);
int __fastcall UnSubscribePositionChange(const UnicodeString aSymbol, const bool aAck = False);
int __fastcall SubscribeMarginMode(const bool aAck = False);
int __fastcall UnSubscribeMarginMode(const bool aAck = False);
int __fastcall SubscribeCrossMarginLeverage(const bool aAck = False);
int __fastcall UnSubscribeCrossMarginLeverage(const bool aAck = False);
void __fastcall QueueClear();
```

