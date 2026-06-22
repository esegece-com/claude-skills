# TIdIPMCastServer

unit: IdIPMCastServer

Add `IdIPMCastServer` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Binding: TIdSocketHandle (read-only)` | [TIdSocketHandle](../types/TIdSocketHandle.md) | `__property TIdSocketHandle * Binding /* read-only */;` |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `BoundIP: String` | `String` | `__property UnicodeString BoundIP;` |
| `BoundPort: TIdPort` | `TIdPort` | `__property TIdPort * BoundPort;` |
| `Loopback: Boolean` | `Boolean` | `__property bool Loopback;` |
| `MulticastGroup: string` | `string` | `__property UnicodeString MulticastGroup;` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](../types/TIdIPVersion.md) | `__property TIdIPVersion * IPVersion;` |
| `Port: TIdPort` | `TIdPort` | `__property TIdPort * Port;` |
| `ReuseSocket: TIdReuseSocket` | [TIdReuseSocket](../types/TIdReuseSocket.md) | `__property TIdReuseSocket * ReuseSocket;` |
| `TimeToLive: Byte` | `Byte` | `__property unsigned char TimeToLive;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
procedure Send(const AData: string; AByteEncoding: IIdTextEncoding = nil ; ASrcEncoding: IIdTextEncoding = nil );
function IsValidMulticastGroup(const Value: string): Boolean;
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Send(const UnicodeString AData, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ASrcEncoding = nil);
bool __fastcall IsValidMulticastGroup(const UnicodeString Value);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

