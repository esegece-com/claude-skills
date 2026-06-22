# TsgcWSAPI_Bitmex

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Bitmex: TsgcWSBitmex_Options` | [TsgcWSBitmex_Options](../types/TsgcWSBitmex_Options.md) | `__property TsgcWSBitmex_Options * Bitmex;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_Bitmex_Rest` | [TsgcHTTP_API_Bitmex_Rest](../types/TsgcHTTP_API_Bitmex_Rest.md) | `__property TsgcHTTP_API_Bitmex_Rest * REST_API;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnBitmexConnect: TsgcWSBitmexConnectEvent` | [TsgcWSBitmexConnectEvent](../types/TsgcWSBitmexConnectEvent.md) | `__property TsgcWSBitmexConnectEvent OnBitmexConnect;` |
| `OnBitmexSubscribed: TsgcWSBitmexSubscribedEvent` | [TsgcWSBitmexSubscribedEvent](../types/TsgcWSBitmexSubscribedEvent.md) | `__property TsgcWSBitmexSubscribedEvent OnBitmexSubscribed;` |
| `OnBitmexUnsubscribed: TsgcWSBitmexUnsubscribedEvent` | [TsgcWSBitmexUnsubscribedEvent](../types/TsgcWSBitmexUnsubscribedEvent.md) | `__property TsgcWSBitmexUnsubscribedEvent OnBitmexUnsubscribed;` |
| `OnBitmexMessage: TsgcWSBitmexMessageEvent` | [TsgcWSBitmexMessageEvent](../types/TsgcWSBitmexMessageEvent.md) | `__property TsgcWSBitmexMessageEvent OnBitmexMessage;` |
| `OnBitmexAuthenticated: TsgcWSBitmexAuthenticatedEvent` | [TsgcWSBitmexAuthenticatedEvent](../types/TsgcWSBitmexAuthenticatedEvent.md) | `__property TsgcWSBitmexAuthenticatedEvent OnBitmexAuthenticated;` |
| `OnBitmexError: TsgcWSBitmexErrorEvent` | [TsgcWSBitmexErrorEvent](../types/TsgcWSBitmexErrorEvent.md) | `__property TsgcWSBitmexErrorEvent OnBitmexError;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnBitmexHTTPException: TsgcWSBitmexHTTPExceptionEvent` | [TsgcWSBitmexHTTPExceptionEvent](../types/TsgcWSBitmexHTTPExceptionEvent.md) | `__property TsgcWSBitmexHTTPExceptionEvent OnBitmexHTTPException;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure Subscribe(aTopic: TwsBitmexTopics; const aSymbol: String = '');
procedure Unsubscribe(aTopic: TwsBitmexTopics; const aSymbol: String = '');
procedure Authenticate;
procedure CancelAllAfter(aTimeout: Integer);
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Subscribe(TwsBitmexTopics * aTopic, const UnicodeString aSymbol = '');
void __fastcall Unsubscribe(TwsBitmexTopics * aTopic, const UnicodeString aSymbol = '');
void __fastcall Authenticate();
void __fastcall CancelAllAfter(int aTimeout);
void __fastcall QueueClear();
```

