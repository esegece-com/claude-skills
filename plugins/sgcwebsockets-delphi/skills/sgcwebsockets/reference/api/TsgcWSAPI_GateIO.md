# TsgcWSAPI_GateIO

unit: sgcWebSocket_APIs
Edition: Standard

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `GateIO: TsgcWSGateIO_Options` | [TsgcWSGateIO_Options](../types/TsgcWSGateIO_Options.md) | `__property TsgcWSGateIO_Options * GateIO;` |
| `GateIOChannel: TsgcWSGateIOChannel` | [TsgcWSGateIOChannel](../types/TsgcWSGateIOChannel.md) | `__property TsgcWSGateIOChannel * GateIOChannel;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_GateIO` | [TsgcHTTP_API_GateIO](../types/TsgcHTTP_API_GateIO.md) | `__property TsgcHTTP_API_GateIO * REST_API;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnGateIOAuthentication: TsgcWSGateIOAuthenticationEvent` | [TsgcWSGateIOAuthenticationEvent](../types/TsgcWSGateIOAuthenticationEvent.md) | `__property TsgcWSGateIOAuthenticationEvent OnGateIOAuthentication;` |
| `OnGateIOSubscribe: TsgcWSGateIOSubscribeEvent` | [TsgcWSGateIOSubscribeEvent](../types/TsgcWSGateIOSubscribeEvent.md) | `__property TsgcWSGateIOSubscribeEvent OnGateIOSubscribe;` |
| `OnGateIOUnSubscribe: TsgcWSGateIOUnSubscribeEvent` | [TsgcWSGateIOUnSubscribeEvent](../types/TsgcWSGateIOUnSubscribeEvent.md) | `__property TsgcWSGateIOUnSubscribeEvent OnGateIOUnSubscribe;` |
| `OnGateIOData: TsgcWSGateIODataEvent` | [TsgcWSGateIODataEvent](../types/TsgcWSGateIODataEvent.md) | `__property TsgcWSGateIODataEvent OnGateIOData;` |
| `OnGateIOError: TsgcWSGateIOErrorEvent` | [TsgcWSGateIOErrorEvent](../types/TsgcWSGateIOErrorEvent.md) | `__property TsgcWSGateIOErrorEvent OnGateIOError;` |
| `OnGateIOHTTPException: TsgcWSGateIOHTTPExceptionEvent` | [TsgcWSGateIOHTTPExceptionEvent](../types/TsgcWSGateIOHTTPExceptionEvent.md) | `__property TsgcWSGateIOHTTPExceptionEvent OnGateIOHTTPException;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure Ping;
function SubscribeTicker(const aSymbol: string): string;
function UnSubscribeTicker(const aSymbol: string): string;
function SubscribeTrades(const aSymbol: string): string;
function UnSubscribeTrades(const aSymbol: string): string;
function SubscribeCandlesticks(const aSymbol: string; const aInterval: string = '1m'): string;
function UnSubscribeCandlesticks(const aSymbol: string; const aInterval: string = '1m'): string;
function SubscribeOrderBook(const aSymbol: string; const aLevel: string = '20'; const aInterval: string = '100ms'): string;
function UnSubscribeOrderBook(const aSymbol: string; const aLevel: string = '20'; const aInterval: string = '100ms'): string;
function SubscribeOrders(const aSymbol: string): string;
function UnSubscribeOrders(const aSymbol: string): string;
function SubscribeBalances: string;
function UnSubscribeBalances: string;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Ping();
UnicodeString __fastcall SubscribeTicker(const UnicodeString aSymbol);
UnicodeString __fastcall UnSubscribeTicker(const UnicodeString aSymbol);
UnicodeString __fastcall SubscribeTrades(const UnicodeString aSymbol);
UnicodeString __fastcall UnSubscribeTrades(const UnicodeString aSymbol);
UnicodeString __fastcall SubscribeCandlesticks(const UnicodeString aSymbol, const UnicodeString aInterval = '1m');
UnicodeString __fastcall UnSubscribeCandlesticks(const UnicodeString aSymbol, const UnicodeString aInterval = '1m');
UnicodeString __fastcall SubscribeOrderBook(const UnicodeString aSymbol, const UnicodeString aLevel = '20', const UnicodeString aInterval = '100ms');
UnicodeString __fastcall UnSubscribeOrderBook(const UnicodeString aSymbol, const UnicodeString aLevel = '20', const UnicodeString aInterval = '100ms');
UnicodeString __fastcall SubscribeOrders(const UnicodeString aSymbol);
UnicodeString __fastcall UnSubscribeOrders(const UnicodeString aSymbol);
UnicodeString __fastcall SubscribeBalances();
UnicodeString __fastcall UnSubscribeBalances();
void __fastcall QueueClear();
```

