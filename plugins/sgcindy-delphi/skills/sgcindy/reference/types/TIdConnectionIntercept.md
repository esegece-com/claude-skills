# TIdConnectionIntercept

kind: class
unit: IdIntercept

## Properties

| Delphi | Type |
| --- | --- |
| `Connection: TComponent (read-only)` | `TComponent` |
| `IsClient: Boolean (read-only)` | `Boolean` |
| `DataObject: TObject` | `TObject` |
| `DataValue: PtrInt` | `PtrInt` |
| `Data: TObject` | `TObject` |
| `Intercept: TIdConnectionIntercept` | [TIdConnectionIntercept](./TIdConnectionIntercept.md) |

## Events

| Delphi | Type |
| --- | --- |
| `OnConnect: TIdInterceptNotifyEvent` | [TIdInterceptNotifyEvent](./TIdInterceptNotifyEvent.md) |
| `OnDisconnect: TIdInterceptNotifyEvent` | [TIdInterceptNotifyEvent](./TIdInterceptNotifyEvent.md) |
| `OnReceive: TIdInterceptStreamEvent` | [TIdInterceptStreamEvent](./TIdInterceptStreamEvent.md) |
| `OnSend: TIdInterceptStreamEvent` | [TIdInterceptStreamEvent](./TIdInterceptStreamEvent.md) |

## Methods

```pascal
procedure Connect(AConnection: TComponent);
procedure Disconnect;
procedure Receive(var VBuffer: TIdBytes);
procedure Send(var VBuffer: TIdBytes);
```

