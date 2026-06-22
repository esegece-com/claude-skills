# TsgcWSAPI_Coinbase

unit: sgcWebSocket_APIs
Edition: Standard

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Coinbase: TsgcWSCoinbase_Options` | [TsgcWSCoinbase_Options](../types/TsgcWSCoinbase_Options.md) | `__property TsgcWSCoinbase_Options * Coinbase;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_Coinbase_Rest` | [TsgcHTTP_API_Coinbase_Rest](../types/TsgcHTTP_API_Coinbase_Rest.md) | `__property TsgcHTTP_API_Coinbase_Rest * REST_API;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnCoinbaseSubscriptions: TsgcWSCoinbaseSubscriptionsEvent` | [TsgcWSCoinbaseSubscriptionsEvent](../types/TsgcWSCoinbaseSubscriptionsEvent.md) | `__property TsgcWSCoinbaseSubscriptionsEvent OnCoinbaseSubscriptions;` |
| `OnCoinbaseHeartbeats: TsgcWSCoinbaseHeartbeatsEvent` | [TsgcWSCoinbaseHeartbeatsEvent](../types/TsgcWSCoinbaseHeartbeatsEvent.md) | `__property TsgcWSCoinbaseHeartbeatsEvent OnCoinbaseHeartbeats;` |
| `OnCoinbaseMessage: TsgcWSCoinbaseMessageEvent` | [TsgcWSCoinbaseMessageEvent](../types/TsgcWSCoinbaseMessageEvent.md) | `__property TsgcWSCoinbaseMessageEvent OnCoinbaseMessage;` |
| `OnCoinbaseError: TsgcWSCoinbaseErrorEvent` | [TsgcWSCoinbaseErrorEvent](../types/TsgcWSCoinbaseErrorEvent.md) | `__property TsgcWSCoinbaseErrorEvent OnCoinbaseError;` |
| `OnCoinbaseHTTPException: TsgcWSCoinbaseHTTPExceptionEvent` | [TsgcWSCoinbaseHTTPExceptionEvent](../types/TsgcWSCoinbaseHTTPExceptionEvent.md) | `__property TsgcWSCoinbaseHTTPExceptionEvent OnCoinbaseHTTPException;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure SubscribeHeartBeat;
procedure UnSubscribeHeartBeat;
procedure SubscribeStatus(const aProductId: string);
procedure UnSubscribeStatus(const aProductId: string);
procedure SubscribeCandles(const aProductId: string);
procedure UnSubscribeCandles(const aProductId: string);
procedure SubscribeMarketTrades(const aProductId: string);
procedure UnSubscribeMarketTrades(const aProductId: string);
procedure SubscribeTicker(const aProductId: string);
procedure UnSubscribeTicker(const aProductId: string);
procedure SubscribeTickerBatch(const aProductId: string);
procedure UnSubscribeTickerBatch(const aProductId: string);
procedure SubscribeLevel2(const aProductId: string);
procedure UnSubscribeLevel2(const aProductId: string);
procedure SubscribeUser(const aProductId: string);
procedure UnSubscribeUser(const aProductId: string);
procedure SubscribeFuturesBalanceSummary;
procedure UnSubscribeFuturesBalanceSummary;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall SubscribeHeartBeat();
void __fastcall UnSubscribeHeartBeat();
void __fastcall SubscribeStatus(const UnicodeString aProductId);
void __fastcall UnSubscribeStatus(const UnicodeString aProductId);
void __fastcall SubscribeCandles(const UnicodeString aProductId);
void __fastcall UnSubscribeCandles(const UnicodeString aProductId);
void __fastcall SubscribeMarketTrades(const UnicodeString aProductId);
void __fastcall UnSubscribeMarketTrades(const UnicodeString aProductId);
void __fastcall SubscribeTicker(const UnicodeString aProductId);
void __fastcall UnSubscribeTicker(const UnicodeString aProductId);
void __fastcall SubscribeTickerBatch(const UnicodeString aProductId);
void __fastcall UnSubscribeTickerBatch(const UnicodeString aProductId);
void __fastcall SubscribeLevel2(const UnicodeString aProductId);
void __fastcall UnSubscribeLevel2(const UnicodeString aProductId);
void __fastcall SubscribeUser(const UnicodeString aProductId);
void __fastcall UnSubscribeUser(const UnicodeString aProductId);
void __fastcall SubscribeFuturesBalanceSummary();
void __fastcall UnSubscribeFuturesBalanceSummary();
void __fastcall QueueClear();
```

