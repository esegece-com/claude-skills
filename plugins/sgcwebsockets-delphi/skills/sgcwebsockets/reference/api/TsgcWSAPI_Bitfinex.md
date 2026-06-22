# TsgcWSAPI_Bitfinex

unit: sgcWebSocket_APIs
Edition: Standard

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
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
| `OnBitfinexConnect: TsgcWSBitfinexConnectEvent` | [TsgcWSBitfinexConnectEvent](../types/TsgcWSBitfinexConnectEvent.md) | `__property TsgcWSBitfinexConnectEvent OnBitfinexConnect;` |
| `OnBitfinexAuth: TsgcWSBitfinexAuthEvent` | [TsgcWSBitfinexAuthEvent](../types/TsgcWSBitfinexAuthEvent.md) | `__property TsgcWSBitfinexAuthEvent OnBitfinexAuth;` |
| `OnBitfinexUnauth: TsgcWSBitfinexUnauthEvent` | [TsgcWSBitfinexUnauthEvent](../types/TsgcWSBitfinexUnauthEvent.md) | `__property TsgcWSBitfinexUnauthEvent OnBitfinexUnauth;` |
| `OnBitfinexInfoMsg: TsgcWSBifinexInfoMessageEvent` | [TsgcWSBifinexInfoMessageEvent](../types/TsgcWSBifinexInfoMessageEvent.md) | `__property TsgcWSBifinexInfoMessageEvent OnBitfinexInfoMsg;` |
| `OnBitfinexSubscribed: TsgcWSBitfinexSubscribedEvent` | [TsgcWSBitfinexSubscribedEvent](../types/TsgcWSBitfinexSubscribedEvent.md) | `__property TsgcWSBitfinexSubscribedEvent OnBitfinexSubscribed;` |
| `OnBitfinexUnSubscribed: TsgcWSBitfinexUnSubscribedEvent` | [TsgcWSBitfinexUnSubscribedEvent](../types/TsgcWSBitfinexUnSubscribedEvent.md) | `__property TsgcWSBitfinexUnSubscribedEvent OnBitfinexUnSubscribed;` |
| `OnBitfinexUpdate: TsgcWSBitfinexUpdate` | [TsgcWSBitfinexUpdate](../types/TsgcWSBitfinexUpdate.md) | `__property TsgcWSBitfinexUpdate * OnBitfinexUpdate;` |
| `OnBitfinexError: TsgcWSBitfinexErrorEvent` | [TsgcWSBitfinexErrorEvent](../types/TsgcWSBitfinexErrorEvent.md) | `__property TsgcWSBitfinexErrorEvent OnBitfinexError;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |

## Methods

Delphi

```pascal
procedure Ping;
procedure Configuration(aFlags: Integer);
procedure Authenticate(aAPIKey, aAuthPayload, aAuthNonce, aAuthSig: String);
procedure UnAuthenticate;
procedure SubscribeTicker(const aSymbol: String);
procedure UnSubscribeTicker(const aChanId: Integer);
procedure SubscribeTrades(const aSymbol: String);
procedure UnSubscribeTrades(const aChanId: Integer);
procedure SubscribeOrderBook(const aPair: String; aPrecision: TsgcWSBitfinexPrecision = P0; aFrequency: TsgcWSBitfinexFrequency = F0; aLength: Integer = 25);
procedure UnSubscribeOrderBook(aChanId: Integer);
procedure SubscribeRawOrderBook(const aPair: String);
procedure UnSubscribeRawOrderBook(aChanId: Integer);
procedure SubscribeCandles(const aKey: String);
procedure UnSubscribeCandles(aChanId: Integer);
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Ping();
void __fastcall Configuration(int aFlags);
void __fastcall Authenticate(UnicodeString aAPIKey, UnicodeString aAuthPayload, UnicodeString aAuthNonce, UnicodeString aAuthSig);
void __fastcall UnAuthenticate();
void __fastcall SubscribeTicker(const UnicodeString aSymbol);
void __fastcall UnSubscribeTicker(const int aChanId);
void __fastcall SubscribeTrades(const UnicodeString aSymbol);
void __fastcall UnSubscribeTrades(const int aChanId);
void __fastcall SubscribeOrderBook(const UnicodeString aPair, TsgcWSBitfinexPrecision * aPrecision = P0, TsgcWSBitfinexFrequency * aFrequency = F0, int aLength = 25);
void __fastcall UnSubscribeOrderBook(int aChanId);
void __fastcall SubscribeRawOrderBook(const UnicodeString aPair);
void __fastcall UnSubscribeRawOrderBook(int aChanId);
void __fastcall SubscribeCandles(const UnicodeString aKey);
void __fastcall UnSubscribeCandles(int aChanId);
void __fastcall QueueClear();
```

