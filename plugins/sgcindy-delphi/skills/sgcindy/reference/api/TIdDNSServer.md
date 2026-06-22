# TIdDNSServer

unit: IdDNSServer

Add `IdDNSServer` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `AccessList: TStrings` | `TStrings` | `__property TStrings * AccessList;` |
| `Bindings: TIdSocketHandles` | [TIdSocketHandles](../types/TIdSocketHandles.md) | `__property TIdSocketHandles * Bindings;` |
| `TCPACLActive: Boolean` | `Boolean` | `__property bool TCPACLActive;` |
| `ServerType: TDNSServerTypes` | [TDNSServerTypes](../types/TDNSServerTypes.md) | `__property TDNSServerTypes * ServerType;` |
| `TCPTunnel: TIdDNS_TCPServer` | [TIdDNS_TCPServer](../types/TIdDNS_TCPServer.md) | `__property TIdDNS_TCPServer * TCPTunnel;` |
| `UDPTunnel: TIdDNS_UDPServer` | [TIdDNS_UDPServer](../types/TIdDNS_UDPServer.md) | `__property TIdDNS_UDPServer * UDPTunnel;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
procedure CheckIfExpire(Sender: TObject);
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall CheckIfExpire(TObject * Sender);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

