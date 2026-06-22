# TIdServerIOHandler

kind: class
unit: IdServerIOHandler

## Properties

| Delphi | Type |
| --- | --- |
| `WorkTarget: TIdComponent` | [TIdComponent](./TIdComponent.md) |
| `Version: string (read-only)` | `string` |

## Events

| Delphi | Type |
| --- | --- |
| `OnSocketAccept: TNotifyEvent` | `TNotifyEvent` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](./TIdStatusEvent.md) |

## Methods

```pascal
function Accept( ASocket: TIdSocketHandle; AListenerThread: TIdThread; AYarn: TIdYarn ): TIdIOHandler;
procedure Listen(ASocket: TIdSocketHandle);
procedure StopListening;
procedure SetServer(const aValue: TObject);
function MakeClientIOHandler(AYarn: TIdYarn): TIdIOHandler;
procedure Init;
procedure Shutdown;
procedure SetScheduler(AScheduler: TIdScheduler);
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

