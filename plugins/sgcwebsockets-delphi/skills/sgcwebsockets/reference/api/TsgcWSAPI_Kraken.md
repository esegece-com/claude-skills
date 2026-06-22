# TsgcWSAPI_Kraken

unit: sgcWebSocket_APIs
Edition: Standard

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Kraken: TsgcWSKraken_Options` | [TsgcWSKraken_Options](../types/TsgcWSKraken_Options.md) | `__property TsgcWSKraken_Options * Kraken;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_Kraken_Rest` | [TsgcHTTP_API_Kraken_Rest](../types/TsgcHTTP_API_Kraken_Rest.md) | `__property TsgcHTTP_API_Kraken_Rest * REST_API;` |
| `FormatCurrency: String` | `String` | `__property UnicodeString FormatCurrency;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnKrakenConnect: TsgcWSKrakenConnectEvent` | [TsgcWSKrakenConnectEvent](../types/TsgcWSKrakenConnectEvent.md) | `__property TsgcWSKrakenConnectEvent OnKrakenConnect;` |
| `OnKrakenSystemStatus: TsgcWSKrakenSystemStatusEvent` | [TsgcWSKrakenSystemStatusEvent](../types/TsgcWSKrakenSystemStatusEvent.md) | `__property TsgcWSKrakenSystemStatusEvent OnKrakenSystemStatus;` |
| `OnKrakenSubscribed: TsgcWSKrakenSubscribedEvent` | [TsgcWSKrakenSubscribedEvent](../types/TsgcWSKrakenSubscribedEvent.md) | `__property TsgcWSKrakenSubscribedEvent OnKrakenSubscribed;` |
| `OnKrakenUnSubscribed: TsgcWSKrakenUnSubscribedEvent` | [TsgcWSKrakenUnSubscribedEvent](../types/TsgcWSKrakenUnSubscribedEvent.md) | `__property TsgcWSKrakenUnSubscribedEvent OnKrakenUnSubscribed;` |
| `OnKrakenSubscriptionError: TsgcWSKrakenSubscriptionError` | [TsgcWSKrakenSubscriptionError](../types/TsgcWSKrakenSubscriptionError.md) | `__property TsgcWSKrakenSubscriptionError * OnKrakenSubscriptionError;` |
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
procedure SubscribeTicker(const aPairs: Array of Const; aReqId: Integer = 0);
procedure UnSubscribeTicker(const aPairs: Array of Const; aReqId: Integer = 0);
procedure SubscribeOHLC(const aPairs: Array of Const; aInterval: TsgcWSKrakenInterval; aReqId: Integer = 0);
procedure UnSubscribeOHLC(const aPairs: Array of Const; aInterval: TsgcWSKrakenInterval; aReqId: Integer = 0);
procedure SubscribeTrade(const aPairs: Array of Const; aReqId: Integer = 0);
procedure UnSubscribeTrade(const aPairs: Array of Const; aReqId: Integer = 0);
procedure SubscribeBook(const aPairs: Array of Const; aDepth: TsgcWSKrakenDepth; aReqId: Integer = 0);
procedure UnSubscribeBook(const aPairs: Array of Const; aDepth: TsgcWSKrakenDepth; aReqId: Integer = 0);
procedure SubscribeSpread(const aPairs: Array of Const; aReqId: Integer = 0);
procedure UnSubscribeSpread(const aPairs: Array of Const; aReqId: Integer = 0);
procedure SubscribeAll(const aPairs: Array of Const; aReqId: Integer = 0);
procedure UnSubscribeAll(const aPairs: Array of Const; aReqId: Integer = 0);
procedure UnSubscribe(aChannelId: Int64);
procedure SubscribeOwnTrades(aReqId: Integer = 0);
procedure UnSubscribeOwnTrades(aReqId: Integer = 0);
procedure SubscribeOpenOrders(aReqId: Integer = 0);
procedure UnSubscribeOpenOrders(aReqId: Integer = 0);
procedure AddOrder(aOrder: TsgcWSKrakenOrder; aReqId: Integer = 0);
procedure CancelOrder(const aOrderId: String; aReqId: Integer = 0);
procedure Ping;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall SubscribeTicker(const Array of Const aPairs, int aReqId = 0);
void __fastcall UnSubscribeTicker(const Array of Const aPairs, int aReqId = 0);
void __fastcall SubscribeOHLC(const Array of Const aPairs, TsgcWSKrakenInterval * aInterval, int aReqId = 0);
void __fastcall UnSubscribeOHLC(const Array of Const aPairs, TsgcWSKrakenInterval * aInterval, int aReqId = 0);
void __fastcall SubscribeTrade(const Array of Const aPairs, int aReqId = 0);
void __fastcall UnSubscribeTrade(const Array of Const aPairs, int aReqId = 0);
void __fastcall SubscribeBook(const Array of Const aPairs, TsgcWSKrakenDepth * aDepth, int aReqId = 0);
void __fastcall UnSubscribeBook(const Array of Const aPairs, TsgcWSKrakenDepth * aDepth, int aReqId = 0);
void __fastcall SubscribeSpread(const Array of Const aPairs, int aReqId = 0);
void __fastcall UnSubscribeSpread(const Array of Const aPairs, int aReqId = 0);
void __fastcall SubscribeAll(const Array of Const aPairs, int aReqId = 0);
void __fastcall UnSubscribeAll(const Array of Const aPairs, int aReqId = 0);
void __fastcall UnSubscribe(long long aChannelId);
void __fastcall SubscribeOwnTrades(int aReqId = 0);
void __fastcall UnSubscribeOwnTrades(int aReqId = 0);
void __fastcall SubscribeOpenOrders(int aReqId = 0);
void __fastcall UnSubscribeOpenOrders(int aReqId = 0);
void __fastcall AddOrder(TsgcWSKrakenOrder * aOrder, int aReqId = 0);
void __fastcall CancelOrder(const UnicodeString aOrderId, int aReqId = 0);
void __fastcall Ping();
void __fastcall QueueClear();
```

