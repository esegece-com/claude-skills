# TsgcWSComponent_WSClient

kind: class
unit: sgcWebSocket_Classes

## Properties

| Delphi | Type |
| --- | --- |
| `Active: Boolean` | `Boolean` |
| `BoundIP: string` | `string` |
| `BoundPort: TIdPort` | `TIdPort` |
| `BoundPortMax: TIdPort` | `TIdPort` |
| `BoundPortMin: TIdPort` | `TIdPort` |
| `Host: String` | `String` |
| `Port: Integer` | `Integer` |
| `TLS: Boolean` | `Boolean` |
| `TLSOptions: TsgcWSTLS_Options` | [TsgcWSTLS_Options](./TsgcWSTLS_Options.md) |
| `FreeConnectionOnDestroy: Boolean` | `Boolean` |
| `WatchDog: TsgcWSWatchDogClient_Options` | [TsgcWSWatchDogClient_Options](./TsgcWSWatchDogClient_Options.md) |
| `URL: String` | `String` |
| `Specifications: TsgcWSSpecifications` | [TsgcWSSpecifications](./TsgcWSSpecifications.md) |
| `LogFile: TsgcWSLogFile` | [TsgcWSLogFile](./TsgcWSLogFile.md) |
| `HeartBeat: TsgcWSHeartBeat_Options` | [TsgcWSHeartBeat_Options](./TsgcWSHeartBeat_Options.md) |
| `TCPKeepAlive: TsgcTCPKeepAlive` | [TsgcTCPKeepAlive](./TsgcTCPKeepAlive.md) |
| `Extensions: TsgcWSExtensions` | [TsgcWSExtensions](./TsgcWSExtensions.md) |
| `QueueMessages: Boolean` | `Boolean` |
| `Version: String (read-only)` | `String` |

## Events

| Delphi | Type |
| --- | --- |
| `OnHandshake: TsgcWSHandshakeEvent` | [TsgcWSHandshakeEvent](./TsgcWSHandshakeEvent.md) |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](./TsgcWSConnectEvent.md) |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](./TsgcWSDisconnectEvent.md) |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](./TsgcWSMessageEvent.md) |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](./TsgcWSBinaryEvent.md) |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](./TsgcWSFragmentedEvent.md) |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](./TsgcWSErrorEvent.md) |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](./TsgcExceptionEvent.md) |

## Methods

```pascal
procedure RegisterProtocol(aObject: TsgcWSProtocol);
procedure UnRegisterProtocol(aObject: TsgcWSProtocol);
procedure RegisterAPI(aObject: TsgcWSAPI);
procedure UnRegisterAPI(aObject: TsgcWSAPI);
procedure WriteData(const aText: String; const aSize: Integer = 0; const aStreaming: TwsStreaming = stmNone);
function WriteAndWaitData(const aText: String; const aTimeOut: Integer = 10000): string;
procedure EnterCS;
procedure LeaveCS;
function AssignedCS: Boolean;
procedure QueueClear;
```

