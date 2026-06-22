# TsgcWSAPI_Bitstamp

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Bitstamp: TsgcWSBitstamp_Options` | [TsgcWSBitstamp_Options](../types/TsgcWSBitstamp_Options.md) | `__property TsgcWSBitstamp_Options * Bitstamp;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_Bitstamp_Rest` | [TsgcHTTP_API_Bitstamp_Rest](../types/TsgcHTTP_API_Bitstamp_Rest.md) | `__property TsgcHTTP_API_Bitstamp_Rest * REST_API;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |
| `OnBitstampHTTPException: TsgcWSBitstampHTTPExceptionEvent` | [TsgcWSBitstampHTTPExceptionEvent](../types/TsgcWSBitstampHTTPExceptionEvent.md) | `__property TsgcWSBitstampHTTPExceptionEvent OnBitstampHTTPException;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |

## Methods

Delphi

```pascal
procedure SubscribeLiveTicker(const aCurrencyPair: string);
procedure UnSubscribeLiveTicker(const aCurrencyPair: string);
procedure SubscribeLiveOrders(const aCurrencyPair: string);
procedure UnSubscribeLiveOrders(const aCurrencyPair: string);
procedure SubscribeLiveOrderBook(const aCurrencyPair: string);
procedure UnSubscribeLiveOrderBook(const aCurrencyPair: string);
procedure SubscribeLiveDetailOrderBook(const aCurrencyPair: string);
procedure UnSubscribeLiveDetailOrderBook(const aCurrencyPair: string);
procedure SubscribeLiveFullOrderBook(const aCurrencyPair: string);
procedure UnSubscribeLiveFullOrderBook(const aCurrencyPair: string);
procedure SubscribeMyOrders(const aCurrencyPair: string);
procedure UnSubscribeMyOrders(const aCurrencyPair: string);
procedure SubscribeMyTrades(const aCurrencyPair: string);
procedure UnSubscribeMyTrades(const aCurrencyPair: string);
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall SubscribeLiveTicker(const UnicodeString aCurrencyPair);
void __fastcall UnSubscribeLiveTicker(const UnicodeString aCurrencyPair);
void __fastcall SubscribeLiveOrders(const UnicodeString aCurrencyPair);
void __fastcall UnSubscribeLiveOrders(const UnicodeString aCurrencyPair);
void __fastcall SubscribeLiveOrderBook(const UnicodeString aCurrencyPair);
void __fastcall UnSubscribeLiveOrderBook(const UnicodeString aCurrencyPair);
void __fastcall SubscribeLiveDetailOrderBook(const UnicodeString aCurrencyPair);
void __fastcall UnSubscribeLiveDetailOrderBook(const UnicodeString aCurrencyPair);
void __fastcall SubscribeLiveFullOrderBook(const UnicodeString aCurrencyPair);
void __fastcall UnSubscribeLiveFullOrderBook(const UnicodeString aCurrencyPair);
void __fastcall SubscribeMyOrders(const UnicodeString aCurrencyPair);
void __fastcall UnSubscribeMyOrders(const UnicodeString aCurrencyPair);
void __fastcall SubscribeMyTrades(const UnicodeString aCurrencyPair);
void __fastcall UnSubscribeMyTrades(const UnicodeString aCurrencyPair);
void __fastcall QueueClear();
```

