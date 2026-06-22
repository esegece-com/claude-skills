# TsgcWSComponent_Server

kind: class
unit: sgcWebSocket_Classes

## Properties

| Delphi | Type |
| --- | --- |
| `Optimizations: TsgcWSOptimization_Options` | [TsgcWSOptimization_Options](./TsgcWSOptimization_Options.md) |
| `WatchDog: TsgcWSWatchDogServer_Options` | [TsgcWSWatchDogServer_Options](./TsgcWSWatchDogServer_Options.md) |
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
| `OnUnknownProtocol: TsgcWSUnknownProtocolEvent` | [TsgcWSUnknownProtocolEvent](./TsgcWSUnknownProtocolEvent.md) |
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
procedure SetNotifyEvents(const Value: TwsNotifyEvent);
procedure RegisterProtocol(aObject: TsgcWSProtocol);
procedure UnRegisterProtocol(aObject: TsgcWSProtocol);
procedure Broadcast(const aMessage: string; const aChannel: string = ''; const aProtocol: string = ''; const Exclude: String = ''; const Include: String = '');
function WriteData(const aGuid, aMessage: string): Boolean;
function LockList: TList <;
procedure UnLockList;
procedure EnterCS;
procedure LeaveCS;
function AssignedCS: Boolean;
procedure QueueClear;
```

