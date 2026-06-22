# TIdComponent

kind: class
unit: IdComponent

## Properties

| Delphi | Type |
| --- | --- |
| `WorkTarget: TIdComponent` | [TIdComponent](./TIdComponent.md) |
| `Version: string (read-only)` | `string` |

## Events

| Delphi | Type |
| --- | --- |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](./TIdStatusEvent.md) |

## Methods

```pascal
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

