# TsgcWSProtocol_Broker_Server

kind: class
unit: sgcWebSocket_Protocol_Broker_Server

## Properties

| Delphi | Type |
| --- | --- |
| `Server: TsgcWSComponent_Server` | [TsgcWSComponent_Server](./TsgcWSComponent_Server.md) |
| `Protocol: string (read-only)` | `string` |
| `Guid: String` | `String` |
| `MsgType: TwsProtocolMessage` | [TwsProtocolMessage](./TwsProtocolMessage.md) |
| `QueueMessages: Boolean` | `Boolean` |
| `Version: String (read-only)` | `String` |

## Events

| Delphi | Type |
| --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](./TsgcWSConnectEvent.md) |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](./TsgcWSDisconnectEvent.md) |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](./TsgcWSMessageEvent.md) |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](./TsgcWSBinaryEvent.md) |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](./TsgcWSFragmentedEvent.md) |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](./TsgcWSErrorEvent.md) |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](./TsgcExceptionEvent.md) |

## Methods

```pascal
procedure DoRegisterProtocol(aObject: TsgcWSProtocol);
procedure DoUnRegisterProtocol(aObject: TsgcWSProtocol);
procedure RegisterProtocol(aObject: TsgcWSProtocol);
procedure UnRegisterProtocol(aObject: TsgcWSProtocol);
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

