# TsgcWSAPI_Deribit

unit: sgcWebSocket_APIs
Edition: Standard

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Deribit: TsgcWSDeribit_Options` | [TsgcWSDeribit_Options](../types/TsgcWSDeribit_Options.md) | `__property TsgcWSDeribit_Options * Deribit;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_Deribit` | [TsgcHTTP_API_Deribit](../types/TsgcHTTP_API_Deribit.md) | `__property TsgcHTTP_API_Deribit * REST_API;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDeribitAuthentication: TsgcWSDeribitAuthenticationEvent` | [TsgcWSDeribitAuthenticationEvent](../types/TsgcWSDeribitAuthenticationEvent.md) | `__property TsgcWSDeribitAuthenticationEvent OnDeribitAuthentication;` |
| `OnDeribitSubscribe: TsgcWSDeribitSubscribeEvent` | [TsgcWSDeribitSubscribeEvent](../types/TsgcWSDeribitSubscribeEvent.md) | `__property TsgcWSDeribitSubscribeEvent OnDeribitSubscribe;` |
| `OnDeribitUnSubscribe: TsgcWSDeribitUnSubscribeEvent` | [TsgcWSDeribitUnSubscribeEvent](../types/TsgcWSDeribitUnSubscribeEvent.md) | `__property TsgcWSDeribitUnSubscribeEvent OnDeribitUnSubscribe;` |
| `OnDeribitData: TsgcWSDeribitDataEvent` | [TsgcWSDeribitDataEvent](../types/TsgcWSDeribitDataEvent.md) | `__property TsgcWSDeribitDataEvent OnDeribitData;` |
| `OnDeribitError: TsgcWSDeribitErrorEvent` | [TsgcWSDeribitErrorEvent](../types/TsgcWSDeribitErrorEvent.md) | `__property TsgcWSDeribitErrorEvent OnDeribitError;` |
| `OnDeribitHTTPException: TsgcWSDeribitHTTPExceptionEvent` | [TsgcWSDeribitHTTPExceptionEvent](../types/TsgcWSDeribitHTTPExceptionEvent.md) | `__property TsgcWSDeribitHTTPExceptionEvent OnDeribitHTTPException;` |
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
procedure Initialize;
function SubscribeTicker(const aInstrument: string): Integer;
function UnSubscribeTicker(const aInstrument: string): Integer;
function SubscribeTrades(const aInstrument: string): Integer;
function UnSubscribeTrades(const aInstrument: string): Integer;
function SubscribeOrderBook(const aInstrument: string; const aGroup: string = 'none'; aDepth: Integer = 10; const aInterval: string = '100ms'): Integer;
function UnSubscribeOrderBook(const aInstrument: string; const aGroup: string = 'none'; aDepth: Integer = 10; const aInterval: string = '100ms'): Integer;
function SubscribeCandle(const aInstrument: string; const aResolution: string = '1'): Integer;
function UnSubscribeCandle(const aInstrument: string; const aResolution: string = '1'): Integer;
function SubscribePerpetual(const aInstrument: string; const aInterval: string = '100ms'): Integer;
function UnSubscribePerpetual(const aInstrument: string; const aInterval: string = '100ms'): Integer;
function SubscribeBookChange(const aInstrument: string; const aInterval: string = '100ms'): Integer;
function UnSubscribeBookChange(const aInstrument: string; const aInterval: string = '100ms'): Integer;
function SubscribeOrders(const aInstrument: string): Integer;
function UnSubscribeOrders(const aInstrument: string): Integer;
function SubscribePositions(const aCurrency: string; const aKind: string = 'any'): Integer;
function UnSubscribePositions(const aCurrency: string; const aKind: string = 'any'): Integer;
function SubscribeAccountChanges(const aCurrency: string): Integer;
function UnSubscribeAccountChanges(const aCurrency: string): Integer;
function SubscribeUserTrades(const aInstrument: string): Integer;
function UnSubscribeUserTrades(const aInstrument: string): Integer;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Ping();
void __fastcall Initialize();
int __fastcall SubscribeTicker(const UnicodeString aInstrument);
int __fastcall UnSubscribeTicker(const UnicodeString aInstrument);
int __fastcall SubscribeTrades(const UnicodeString aInstrument);
int __fastcall UnSubscribeTrades(const UnicodeString aInstrument);
int __fastcall SubscribeOrderBook(const UnicodeString aInstrument, const UnicodeString aGroup = 'none', int aDepth = 10, const UnicodeString aInterval = '100ms');
int __fastcall UnSubscribeOrderBook(const UnicodeString aInstrument, const UnicodeString aGroup = 'none', int aDepth = 10, const UnicodeString aInterval = '100ms');
int __fastcall SubscribeCandle(const UnicodeString aInstrument, const UnicodeString aResolution = '1');
int __fastcall UnSubscribeCandle(const UnicodeString aInstrument, const UnicodeString aResolution = '1');
int __fastcall SubscribePerpetual(const UnicodeString aInstrument, const UnicodeString aInterval = '100ms');
int __fastcall UnSubscribePerpetual(const UnicodeString aInstrument, const UnicodeString aInterval = '100ms');
int __fastcall SubscribeBookChange(const UnicodeString aInstrument, const UnicodeString aInterval = '100ms');
int __fastcall UnSubscribeBookChange(const UnicodeString aInstrument, const UnicodeString aInterval = '100ms');
int __fastcall SubscribeOrders(const UnicodeString aInstrument);
int __fastcall UnSubscribeOrders(const UnicodeString aInstrument);
int __fastcall SubscribePositions(const UnicodeString aCurrency, const UnicodeString aKind = 'any');
int __fastcall UnSubscribePositions(const UnicodeString aCurrency, const UnicodeString aKind = 'any');
int __fastcall SubscribeAccountChanges(const UnicodeString aCurrency);
int __fastcall UnSubscribeAccountChanges(const UnicodeString aCurrency);
int __fastcall SubscribeUserTrades(const UnicodeString aInstrument);
int __fastcall UnSubscribeUserTrades(const UnicodeString aInstrument);
void __fastcall QueueClear();
```

