# TsgcWSAPI_SocketIO

unit: sgcWebSocket_APIs
Edition: Standard

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `SocketIO: TsgcWSSocketIO_Options` | [TsgcWSSocketIO_Options](../types/TsgcWSSocketIO_Options.md) | `__property TsgcWSSocketIO_Options * SocketIO;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `IO_CloseTimeout: Integer (read-only)` | `Integer` | `__property int IO_CloseTimeout /* read-only */;` |
| `IO_HeartBeatTimeout: Integer (read-only)` | `Integer` | `__property int IO_HeartBeatTimeout /* read-only */;` |
| `IO_SessionId: String (read-only)` | `String` | `__property UnicodeString IO_SessionId /* read-only */;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnHTTPConnectionSSL: TsgcWSOnHTTPConnectionSSL` | [TsgcWSOnHTTPConnectionSSL](../types/TsgcWSOnHTTPConnectionSSL.md) | `__property TsgcWSOnHTTPConnectionSSL OnHTTPConnectionSSL;` |
| `OnHTTPRequest: TsgcWSOnSocketIOHTTPRequest` | [TsgcWSOnSocketIOHTTPRequest](../types/TsgcWSOnSocketIOHTTPRequest.md) | `__property TsgcWSOnSocketIOHTTPRequest OnHTTPRequest;` |
| `OnAfterConnect: TsgcWSOnSocketIOAfterConnect` | [TsgcWSOnSocketIOAfterConnect](../types/TsgcWSOnSocketIOAfterConnect.md) | `__property TsgcWSOnSocketIOAfterConnect OnAfterConnect;` |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
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
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Ping();
void __fastcall QueueClear();
```

