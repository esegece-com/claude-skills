# TIdIPMCastClient

unit: IdIPMCastClient

Add `IdIPMCastClient` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](../types/TIdIPVersion.md) | `__property TIdIPVersion * IPVersion;` |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `Bindings: TIdSocketHandles` | [TIdSocketHandles](../types/TIdSocketHandles.md) | `__property TIdSocketHandles * Bindings;` |
| `BufferSize: Integer` | `Integer` | `__property int BufferSize;` |
| `DefaultPort: integer` | `integer` | `__property int DefaultPort;` |
| `MulticastGroup: string` | `string` | `__property UnicodeString MulticastGroup;` |
| `ReuseSocket: TIdReuseSocket` | [TIdReuseSocket](../types/TIdReuseSocket.md) | `__property TIdReuseSocket * ReuseSocket;` |
| `ThreadedEvent: boolean` | `boolean` | `__property bool ThreadedEvent;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnBeforeBind: TIdSocketHandleEvent` | [TIdSocketHandleEvent](../types/TIdSocketHandleEvent.md) | `__property TIdSocketHandleEvent OnBeforeBind;` |
| `OnAfterBind: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAfterBind;` |
| `OnIPMCastRead: TIPMCastReadEvent` | [TIPMCastReadEvent](../types/TIPMCastReadEvent.md) | `__property TIPMCastReadEvent OnIPMCastRead;` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
function IsValidMulticastGroup(const Value: string): Boolean;
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
bool __fastcall IsValidMulticastGroup(const UnicodeString Value);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

