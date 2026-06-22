# TIdCompressionIntercept

unit: IdCompressionIntercept

Add `IdCompressionIntercept` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `CompressionLevel: TIdCompressionLevel` | `TIdCompressionLevel` | `__property TIdCompressionLevel * CompressionLevel;` |
| `Connection: TComponent (read-only)` | `TComponent` | `__property TComponent * Connection /* read-only */;` |
| `IsClient: Boolean (read-only)` | `Boolean` | `__property bool IsClient /* read-only */;` |
| `DataObject: TObject` | `TObject` | `__property TObject * DataObject;` |
| `DataValue: PtrInt` | `PtrInt` | `__property PtrInt DataValue;` |
| `Data: TObject` | `TObject` | `__property TObject * Data;` |
| `Intercept: TIdConnectionIntercept` | [TIdConnectionIntercept](../types/TIdConnectionIntercept.md) | `__property TIdConnectionIntercept * Intercept;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TIdInterceptNotifyEvent` | [TIdInterceptNotifyEvent](../types/TIdInterceptNotifyEvent.md) | `__property TIdInterceptNotifyEvent OnConnect;` |
| `OnDisconnect: TIdInterceptNotifyEvent` | [TIdInterceptNotifyEvent](../types/TIdInterceptNotifyEvent.md) | `__property TIdInterceptNotifyEvent OnDisconnect;` |
| `OnReceive: TIdInterceptStreamEvent` | [TIdInterceptStreamEvent](../types/TIdInterceptStreamEvent.md) | `__property TIdInterceptStreamEvent OnReceive;` |
| `OnSend: TIdInterceptStreamEvent` | [TIdInterceptStreamEvent](../types/TIdInterceptStreamEvent.md) | `__property TIdInterceptStreamEvent OnSend;` |

## Methods

Delphi

```pascal
procedure Disconnect;
procedure Receive(var VBuffer: TIdBytes);
procedure Send(var VBuffer: TIdBytes);
procedure Connect(AConnection: TComponent);
```

C++Builder

```cpp
void __fastcall Disconnect();
void __fastcall Receive(TIdBytes * &VBuffer);
void __fastcall Send(TIdBytes * &VBuffer);
void __fastcall Connect(TComponent * AConnection);
```

