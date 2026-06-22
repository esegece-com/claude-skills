# TIdBlockCipherIntercept

unit: IdBlockCipherIntercept

Add `IdBlockCipherIntercept` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `BlockSize: Integer` | `Integer` | `__property int BlockSize;` |
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
procedure Receive(var VBuffer: TIdBytes);
procedure Send(var VBuffer: TIdBytes);
procedure CopySettingsFrom (ASrcBlockCipherIntercept: TIdBlockCipherIntercept);
procedure Connect(AConnection: TComponent);
procedure Disconnect;
```

C++Builder

```cpp
void __fastcall Receive(TIdBytes * &VBuffer);
void __fastcall Send(TIdBytes * &VBuffer);
void __fastcall CopySettingsFrom(TIdBlockCipherIntercept * ASrcBlockCipherIntercept);
void __fastcall Connect(TComponent * AConnection);
void __fastcall Disconnect();
```

