# TsgcWSAPI_CryptoCom

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `CryptoCom: TsgcWSCryptoCom_Options` | [TsgcWSCryptoCom_Options](../types/TsgcWSCryptoCom_Options.md) | `__property TsgcWSCryptoCom_Options * CryptoCom;` |
| `Channel: TsgcWSCryptoComChannel` | [TsgcWSCryptoComChannel](../types/TsgcWSCryptoComChannel.md) | `__property TsgcWSCryptoComChannel * Channel;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_CryptoCom` | [TsgcHTTP_API_CryptoCom](../types/TsgcHTTP_API_CryptoCom.md) | `__property TsgcHTTP_API_CryptoCom * REST_API;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnCryptoComAuthentication: TsgcWSCryptoComAuthenticationEvent` | [TsgcWSCryptoComAuthenticationEvent](../types/TsgcWSCryptoComAuthenticationEvent.md) | `__property TsgcWSCryptoComAuthenticationEvent OnCryptoComAuthentication;` |
| `OnCryptoComSubscribe: TsgcWSCryptoComSubscribeEvent` | [TsgcWSCryptoComSubscribeEvent](../types/TsgcWSCryptoComSubscribeEvent.md) | `__property TsgcWSCryptoComSubscribeEvent OnCryptoComSubscribe;` |
| `OnCryptoComUnSubscribe: TsgcWSCryptoComUnSubscribeEvent` | [TsgcWSCryptoComUnSubscribeEvent](../types/TsgcWSCryptoComUnSubscribeEvent.md) | `__property TsgcWSCryptoComUnSubscribeEvent OnCryptoComUnSubscribe;` |
| `OnCryptoComData: TsgcWSCryptoComDataEvent` | [TsgcWSCryptoComDataEvent](../types/TsgcWSCryptoComDataEvent.md) | `__property TsgcWSCryptoComDataEvent OnCryptoComData;` |
| `OnCryptoComError: TsgcWSCryptoComErrorEvent` | [TsgcWSCryptoComErrorEvent](../types/TsgcWSCryptoComErrorEvent.md) | `__property TsgcWSCryptoComErrorEvent OnCryptoComError;` |
| `OnCryptoComHTTPException: TsgcWSCryptoComHTTPExceptionEvent` | [TsgcWSCryptoComHTTPExceptionEvent](../types/TsgcWSCryptoComHTTPExceptionEvent.md) | `__property TsgcWSCryptoComHTTPExceptionEvent OnCryptoComHTTPException;` |
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
function SubscribeTicker(const aInstrumentName: string): Integer;
function UnSubscribeTicker(const aInstrumentName: string): Integer;
function SubscribeTrade(const aInstrumentName: string): Integer;
function UnSubscribeTrade(const aInstrumentName: string): Integer;
function SubscribeCandlestick(const aInstrumentName: string; const aInterval: string = '5m'): Integer;
function UnSubscribeCandlestick(const aInstrumentName: string; const aInterval: string = '5m'): Integer;
function SubscribeBook(const aInstrumentName: string; const aDepth: string = '10'): Integer;
function UnSubscribeBook(const aInstrumentName: string; const aDepth: string = '10'): Integer;
function SubscribeOrders(const aInstrumentName: string = ''): Integer;
function UnSubscribeOrders(const aInstrumentName: string = ''): Integer;
function SubscribeUserTrades(const aInstrumentName: string = ''): Integer;
function UnSubscribeUserTrades(const aInstrumentName: string = ''): Integer;
function SubscribeBalance: Integer;
function UnSubscribeBalance: Integer;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Ping();
void __fastcall Initialize();
int __fastcall SubscribeTicker(const UnicodeString aInstrumentName);
int __fastcall UnSubscribeTicker(const UnicodeString aInstrumentName);
int __fastcall SubscribeTrade(const UnicodeString aInstrumentName);
int __fastcall UnSubscribeTrade(const UnicodeString aInstrumentName);
int __fastcall SubscribeCandlestick(const UnicodeString aInstrumentName, const UnicodeString aInterval = '5m');
int __fastcall UnSubscribeCandlestick(const UnicodeString aInstrumentName, const UnicodeString aInterval = '5m');
int __fastcall SubscribeBook(const UnicodeString aInstrumentName, const UnicodeString aDepth = '10');
int __fastcall UnSubscribeBook(const UnicodeString aInstrumentName, const UnicodeString aDepth = '10');
int __fastcall SubscribeOrders(const UnicodeString aInstrumentName = '');
int __fastcall UnSubscribeOrders(const UnicodeString aInstrumentName = '');
int __fastcall SubscribeUserTrades(const UnicodeString aInstrumentName = '');
int __fastcall UnSubscribeUserTrades(const UnicodeString aInstrumentName = '');
int __fastcall SubscribeBalance();
int __fastcall UnSubscribeBalance();
void __fastcall QueueClear();
```

