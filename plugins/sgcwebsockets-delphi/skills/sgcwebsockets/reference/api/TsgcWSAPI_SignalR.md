# TsgcWSAPI_SignalR

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `SignalR: TsgcWSSignalR_Options` | [TsgcWSSignalR_Options](../types/TsgcWSSignalR_Options.md) | `__property TsgcWSSignalR_Options * SignalR;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `Negotiation: TsgcWSSignalR_Negotiation` | [TsgcWSSignalR_Negotiation](../types/TsgcWSSignalR_Negotiation.md) | `__property TsgcWSSignalR_Negotiation * Negotiation;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnSignalRConnect: TsgcWSSignalRConnectEvent` | [TsgcWSSignalRConnectEvent](../types/TsgcWSSignalRConnectEvent.md) | `__property TsgcWSSignalRConnectEvent OnSignalRConnect;` |
| `OnSignalRMessage: TsgcWSSignalRMessageEvent` | [TsgcWSSignalRMessageEvent](../types/TsgcWSSignalRMessageEvent.md) | `__property TsgcWSSignalRMessageEvent OnSignalRMessage;` |
| `OnSignalRBinary: TsgcWSSignalRBinaryEvent` | [TsgcWSSignalRBinaryEvent](../types/TsgcWSSignalRBinaryEvent.md) | `__property TsgcWSSignalRBinaryEvent OnSignalRBinary;` |
| `OnSignalRKeepAlive: TsgcWSSignalRKeepAliveEvent` | [TsgcWSSignalRKeepAliveEvent](../types/TsgcWSSignalRKeepAliveEvent.md) | `__property TsgcWSSignalRKeepAliveEvent OnSignalRKeepAlive;` |
| `OnSignalRResult: TsgcWSSignalRResultEvent` | [TsgcWSSignalRResultEvent](../types/TsgcWSSignalRResultEvent.md) | `__property TsgcWSSignalRResultEvent OnSignalRResult;` |
| `OnSignalRError: TsgcWSSignalRErrorEvent` | [TsgcWSSignalRErrorEvent](../types/TsgcWSSignalRErrorEvent.md) | `__property TsgcWSSignalRErrorEvent OnSignalRError;` |
| `OnSignalRDisconnect: TsgcWSSignalRDisconnectEvent` | [TsgcWSSignalRDisconnectEvent](../types/TsgcWSSignalRDisconnectEvent.md) | `__property TsgcWSSignalRDisconnectEvent OnSignalRDisconnect;` |
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
procedure WriteData(const aText: String);
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall WriteData(const UnicodeString aText);
void __fastcall QueueClear();
```

