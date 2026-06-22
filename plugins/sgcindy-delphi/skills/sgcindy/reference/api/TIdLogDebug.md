# TIdLogDebug

unit: IdLogDebug

Add `IdLogDebug` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `LogTime: Boolean` | `Boolean` | `__property bool LogTime;` |
| `ReplaceCRLF: Boolean` | `Boolean` | `__property bool ReplaceCRLF;` |
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
procedure Open;
procedure Close;
procedure Connect(AConnection: TComponent);
procedure Disconnect;
procedure Receive(var ABuffer: TIdBytes);
procedure Send(var ABuffer: TIdBytes);
```

C++Builder

```cpp
void __fastcall Open();
void __fastcall Close();
void __fastcall Connect(TComponent * AConnection);
void __fastcall Disconnect();
void __fastcall Receive(TIdBytes * &ABuffer);
void __fastcall Send(TIdBytes * &ABuffer);
```

