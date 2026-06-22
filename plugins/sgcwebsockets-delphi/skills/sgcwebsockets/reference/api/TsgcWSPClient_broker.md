# TsgcWSPClient_broker

unit: sgcWebSocket_Protocols
Edition: Professional

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `WSBrokerMessageWrite: TsgcWSBrokerMessage` | [TsgcWSBrokerMessage](../types/TsgcWSBrokerMessage.md) | `__property TsgcWSBrokerMessage * WSBrokerMessageWrite;` |
| `WSBrokerBinaryWrite: TsgcWSBrokerBinary` | [TsgcWSBrokerBinary](../types/TsgcWSBrokerBinary.md) | `__property TsgcWSBrokerBinary * WSBrokerBinaryWrite;` |
| `Protocol: string (read-only)` | `string` | `__property UnicodeString Protocol /* read-only */;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `MsgType: TwsProtocolMessage` | [TwsProtocolMessage](../types/TwsProtocolMessage.md) | `__property TwsProtocolMessage * MsgType;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
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
procedure DoRegisterProtocol(aObject: TsgcWSProtocol);
procedure DoUnRegisterProtocol(aObject: TsgcWSProtocol);
procedure RegisterProtocol(aObject: TsgcWSProtocol);
procedure UnRegisterProtocol(aObject: TsgcWSProtocol);
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall DoRegisterProtocol(TsgcWSProtocol * aObject);
void __fastcall DoUnRegisterProtocol(TsgcWSProtocol * aObject);
void __fastcall RegisterProtocol(TsgcWSProtocol * aObject);
void __fastcall UnRegisterProtocol(TsgcWSProtocol * aObject);
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

