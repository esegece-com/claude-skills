# TsgcWSAPI_Bitget

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Bitget: TsgcWSBitget_Options` | [TsgcWSBitget_Options](../types/TsgcWSBitget_Options.md) | `__property TsgcWSBitget_Options * Bitget;` |
| `BitgetChannel: TsgcWSBitgetChannel` | [TsgcWSBitgetChannel](../types/TsgcWSBitgetChannel.md) | `__property TsgcWSBitgetChannel * BitgetChannel;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_Bitget` | [TsgcHTTP_API_Bitget](../types/TsgcHTTP_API_Bitget.md) | `__property TsgcHTTP_API_Bitget * REST_API;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnBitgetAuthentication: TsgcWSBitgetAuthenticationEvent` | [TsgcWSBitgetAuthenticationEvent](../types/TsgcWSBitgetAuthenticationEvent.md) | `__property TsgcWSBitgetAuthenticationEvent OnBitgetAuthentication;` |
| `OnBitgetSubscribe: TsgcWSBitgetSubscribeEvent` | [TsgcWSBitgetSubscribeEvent](../types/TsgcWSBitgetSubscribeEvent.md) | `__property TsgcWSBitgetSubscribeEvent OnBitgetSubscribe;` |
| `OnBitgetUnSubscribe: TsgcWSBitgetUnSubscribeEvent` | [TsgcWSBitgetUnSubscribeEvent](../types/TsgcWSBitgetUnSubscribeEvent.md) | `__property TsgcWSBitgetUnSubscribeEvent OnBitgetUnSubscribe;` |
| `OnBitgetData: TsgcWSBitgetDataEvent` | [TsgcWSBitgetDataEvent](../types/TsgcWSBitgetDataEvent.md) | `__property TsgcWSBitgetDataEvent OnBitgetData;` |
| `OnBitgetError: TsgcWSBitgetErrorEvent` | [TsgcWSBitgetErrorEvent](../types/TsgcWSBitgetErrorEvent.md) | `__property TsgcWSBitgetErrorEvent OnBitgetError;` |
| `OnBitgetHTTPException: TsgcWSBitgetHTTPExceptionEvent` | [TsgcWSBitgetHTTPExceptionEvent](../types/TsgcWSBitgetHTTPExceptionEvent.md) | `__property TsgcWSBitgetHTTPExceptionEvent OnBitgetHTTPException;` |
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
function SubscribeTicker(const aInstId: string; const aInstType: string = 'SPOT'): string;
function UnSubscribeTicker(const aInstId: string; const aInstType: string = 'SPOT'): string;
function SubscribeTrade(const aInstId: string; const aInstType: string = 'SPOT'): string;
function UnSubscribeTrade(const aInstId: string; const aInstType: string = 'SPOT'): string;
function SubscribeCandle(const aInstId: string; const aChannel: string = 'candle1m'; const aInstType: string = 'SPOT'): string;
function UnSubscribeCandle(const aInstId: string; const aChannel: string = 'candle1m'; const aInstType: string = 'SPOT'): string;
function SubscribeOrderBook(const aInstId: string; const aChannel: string = 'books'; const aInstType: string = 'SPOT'): string;
function UnSubscribeOrderBook(const aInstId: string; const aChannel: string = 'books'; const aInstType: string = 'SPOT'): string;
function SubscribeOrders(const aInstId: string; const aInstType: string = 'SPOT'): string;
function UnSubscribeOrders(const aInstId: string; const aInstType: string = 'SPOT'): string;
function SubscribePositions(const aInstId: string; const aInstType: string = 'USDT-FUTURES'): string;
function UnSubscribePositions(const aInstId: string; const aInstType: string = 'USDT-FUTURES'): string;
function SubscribeAccount(const aCoin: string = ''): string;
function UnSubscribeAccount(const aCoin: string = ''): string;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Ping();
UnicodeString __fastcall SubscribeTicker(const UnicodeString aInstId, const UnicodeString aInstType = 'SPOT');
UnicodeString __fastcall UnSubscribeTicker(const UnicodeString aInstId, const UnicodeString aInstType = 'SPOT');
UnicodeString __fastcall SubscribeTrade(const UnicodeString aInstId, const UnicodeString aInstType = 'SPOT');
UnicodeString __fastcall UnSubscribeTrade(const UnicodeString aInstId, const UnicodeString aInstType = 'SPOT');
UnicodeString __fastcall SubscribeCandle(const UnicodeString aInstId, const UnicodeString aChannel = 'candle1m', const UnicodeString aInstType = 'SPOT');
UnicodeString __fastcall UnSubscribeCandle(const UnicodeString aInstId, const UnicodeString aChannel = 'candle1m', const UnicodeString aInstType = 'SPOT');
UnicodeString __fastcall SubscribeOrderBook(const UnicodeString aInstId, const UnicodeString aChannel = 'books', const UnicodeString aInstType = 'SPOT');
UnicodeString __fastcall UnSubscribeOrderBook(const UnicodeString aInstId, const UnicodeString aChannel = 'books', const UnicodeString aInstType = 'SPOT');
UnicodeString __fastcall SubscribeOrders(const UnicodeString aInstId, const UnicodeString aInstType = 'SPOT');
UnicodeString __fastcall UnSubscribeOrders(const UnicodeString aInstId, const UnicodeString aInstType = 'SPOT');
UnicodeString __fastcall SubscribePositions(const UnicodeString aInstId, const UnicodeString aInstType = 'USDT-FUTURES');
UnicodeString __fastcall UnSubscribePositions(const UnicodeString aInstId, const UnicodeString aInstType = 'USDT-FUTURES');
UnicodeString __fastcall SubscribeAccount(const UnicodeString aCoin = '');
UnicodeString __fastcall UnSubscribeAccount(const UnicodeString aCoin = '');
void __fastcall QueueClear();
```

