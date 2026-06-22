# TIdDNS_TCPServer

kind: class
unit: IdDNSServer

## Properties

| Delphi | Type |
| --- | --- |
| `AccessList: TStrings` | `TStrings` |
| `AccessControl: boolean` | `boolean` |
| `Contexts: TIdContextThreadList (read-only)` | `TIdContextThreadList` |
| `ContextClass: TIdServerContextClass` | [TIdServerContextClass](./TIdServerContextClass.md) |
| `ImplicitIOHandler: Boolean (read-only)` | `Boolean` |
| `ImplicitScheduler: Boolean (read-only)` | `Boolean` |
| `Active: Boolean` | `Boolean` |
| `Bindings: TIdSocketHandles` | [TIdSocketHandles](./TIdSocketHandles.md) |
| `DefaultPort: TIdPort` | `TIdPort` |
| `Intercept: TIdServerIntercept` | [TIdServerIntercept](./TIdServerIntercept.md) |
| `IOHandler: TIdServerIOHandler` | [TIdServerIOHandler](./TIdServerIOHandler.md) |
| `ListenQueue: integer` | `integer` |
| `MaxConnections: Integer` | `Integer` |
| `ReuseSocket: TIdReuseSocket` | [TIdReuseSocket](./TIdReuseSocket.md) |
| `UseNagle: boolean` | `boolean` |
| `TerminateWaitTime: Integer` | `Integer` |
| `Scheduler: TIdScheduler` | [TIdScheduler](./TIdScheduler.md) |
| `WorkTarget: TIdComponent` | [TIdComponent](./TIdComponent.md) |
| `Version: string (read-only)` | `string` |

## Events

| Delphi | Type |
| --- | --- |
| `OnBeforeBind: TIdSocketHandleEvent` | [TIdSocketHandleEvent](./TIdSocketHandleEvent.md) |
| `OnAfterBind: TNotifyEvent` | `TNotifyEvent` |
| `OnBeforeListenerRun: TIdNotifyThreadEvent` | [TIdNotifyThreadEvent](./TIdNotifyThreadEvent.md) |
| `OnContextCreated: TIdServerThreadEvent` | [TIdServerThreadEvent](./TIdServerThreadEvent.md) |
| `OnConnect: TIdServerThreadEvent` | [TIdServerThreadEvent](./TIdServerThreadEvent.md) |
| `OnDisconnect: TIdServerThreadEvent` | [TIdServerThreadEvent](./TIdServerThreadEvent.md) |
| `OnException: TIdServerThreadExceptionEvent` | [TIdServerThreadExceptionEvent](./TIdServerThreadExceptionEvent.md) |
| `OnListenException: TIdListenExceptionEvent` | [TIdListenExceptionEvent](./TIdListenExceptionEvent.md) |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](./TIdStatusEvent.md) |

## Methods

```pascal
procedure StartListening;
procedure StopListening;
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

