# TsgcWSAPI_Kraken_Futures

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Kraken: TsgcWSKrakenFutures_Options` | [TsgcWSKrakenFutures_Options](../types/TsgcWSKrakenFutures_Options.md) | `__property TsgcWSKrakenFutures_Options * Kraken;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_Kraken_Futures_Rest` | [TsgcHTTP_API_Kraken_Futures_Rest](../types/TsgcHTTP_API_Kraken_Futures_Rest.md) | `__property TsgcHTTP_API_Kraken_Futures_Rest * REST_API;` |
| `FormatCurrency: String` | `String` | `__property UnicodeString FormatCurrency;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnKrakenFuturesConnect: TsgcWSKrakenFuturesConnectEvent` | [TsgcWSKrakenFuturesConnectEvent](../types/TsgcWSKrakenFuturesConnectEvent.md) | `__property TsgcWSKrakenFuturesConnectEvent OnKrakenFuturesConnect;` |
| `OnKrakenFuturesSubscribed: TsgcWSKrakenFuturesSubscribedEvent` | [TsgcWSKrakenFuturesSubscribedEvent](../types/TsgcWSKrakenFuturesSubscribedEvent.md) | `__property TsgcWSKrakenFuturesSubscribedEvent OnKrakenFuturesSubscribed;` |
| `OnKrakenFuturesUnSubscribed: TsgcWSKrakenFuturesUnSubscribedEvent` | [TsgcWSKrakenFuturesUnSubscribedEvent](../types/TsgcWSKrakenFuturesUnSubscribedEvent.md) | `__property TsgcWSKrakenFuturesUnSubscribedEvent OnKrakenFuturesUnSubscribed;` |
| `OnKrakenFuturesError: TsgcWSKrakenFuturesErrorEvent` | [TsgcWSKrakenFuturesErrorEvent](../types/TsgcWSKrakenFuturesErrorEvent.md) | `__property TsgcWSKrakenFuturesErrorEvent OnKrakenFuturesError;` |
| `OnKrakenData: TsgcWSKrakenDataEvent` | [TsgcWSKrakenDataEvent](../types/TsgcWSKrakenDataEvent.md) | `__property TsgcWSKrakenDataEvent OnKrakenData;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnKrakenHTTPException: TsgcWSKrakenHTTPExceptionEvent` | [TsgcWSKrakenHTTPExceptionEvent](../types/TsgcWSKrakenHTTPExceptionEvent.md) | `__property TsgcWSKrakenHTTPExceptionEvent OnKrakenHTTPException;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure SubscribeTicker(const aProductIds: Array of Const);
procedure UnSubscribeTicker(const aProductIds: Array of Const);
procedure SubscribeTrade(const aProductIds: Array of Const);
procedure UnSubscribeTrade(const aProductIds: Array of Const);
procedure SubscribeHeartbeat;
procedure UnSubscribeHeartbeat;
procedure SubscribeTickerLite(const aProductIds: Array of Const);
procedure UnSubscribeTickerLite(const aProductIds: Array of Const);
procedure SubscribeBook(const aProductIds: Array of Const);
procedure UnSubscribeBook(const aProductIds: Array of Const);
procedure SubscribeOpenOrdersVerbose;
procedure UnSubscribeOpenOrdersVerbose;
procedure SubscribeOpenPositions;
procedure UnSubscribeOpenPositions;
procedure SubscribeAccountLog;
procedure UnSubscribeAccountLog;
procedure SubscribeFills;
procedure UnSubscribeFills;
procedure SubscribeOpenOrders;
procedure UnSubscribeOpenOrders;
procedure SubscribeAccountBalanceAndMargins;
procedure UnSubscribeAccountBalanceAndMargins;
procedure SubscribeNotifications;
procedure UnSubscribeNotifications;
procedure Ping;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall SubscribeTicker(const Array of Const aProductIds);
void __fastcall UnSubscribeTicker(const Array of Const aProductIds);
void __fastcall SubscribeTrade(const Array of Const aProductIds);
void __fastcall UnSubscribeTrade(const Array of Const aProductIds);
void __fastcall SubscribeHeartbeat();
void __fastcall UnSubscribeHeartbeat();
void __fastcall SubscribeTickerLite(const Array of Const aProductIds);
void __fastcall UnSubscribeTickerLite(const Array of Const aProductIds);
void __fastcall SubscribeBook(const Array of Const aProductIds);
void __fastcall UnSubscribeBook(const Array of Const aProductIds);
void __fastcall SubscribeOpenOrdersVerbose();
void __fastcall UnSubscribeOpenOrdersVerbose();
void __fastcall SubscribeOpenPositions();
void __fastcall UnSubscribeOpenPositions();
void __fastcall SubscribeAccountLog();
void __fastcall UnSubscribeAccountLog();
void __fastcall SubscribeFills();
void __fastcall UnSubscribeFills();
void __fastcall SubscribeOpenOrders();
void __fastcall UnSubscribeOpenOrders();
void __fastcall SubscribeAccountBalanceAndMargins();
void __fastcall UnSubscribeAccountBalanceAndMargins();
void __fastcall SubscribeNotifications();
void __fastcall UnSubscribeNotifications();
void __fastcall Ping();
void __fastcall QueueClear();
```

