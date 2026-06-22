# TIdUnixTimeUDPServer

unit: IdUnixTimeUDPServer

Add `IdUnixTimeUDPServer` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `DefaultPort: TIdPort` | `TIdPort` | `__property TIdPort * DefaultPort;` |
| `ThreadClass: TIdUDPListenerThreadClass` | [TIdUDPListenerThreadClass](../types/TIdUDPListenerThreadClass.md) | `__property TIdUDPListenerThreadClass * ThreadClass;` |
| `Bindings: TIdSocketHandles` | [TIdSocketHandles](../types/TIdSocketHandles.md) | `__property TIdSocketHandles * Bindings;` |
| `ReuseSocket: TIdReuseSocket` | [TIdReuseSocket](../types/TIdReuseSocket.md) | `__property TIdReuseSocket * ReuseSocket;` |
| `ThreadedEvent: boolean` | `boolean` | `__property bool ThreadedEvent;` |
| `Binding: TIdSocketHandle (read-only)` | [TIdSocketHandle](../types/TIdSocketHandle.md) | `__property TIdSocketHandle * Binding /* read-only */;` |
| `ReceiveTimeout: Integer` | `Integer` | `__property int ReceiveTimeout;` |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `BufferSize: Integer` | `Integer` | `__property int BufferSize;` |
| `BroadcastEnabled: Boolean` | `Boolean` | `__property bool BroadcastEnabled;` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](../types/TIdIPVersion.md) | `__property TIdIPVersion * IPVersion;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnBeforeBind: TIdSocketHandleEvent` | [TIdSocketHandleEvent](../types/TIdSocketHandleEvent.md) | `__property TIdSocketHandleEvent OnBeforeBind;` |
| `OnAfterBind: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAfterBind;` |
| `OnUDPRead: TUDPReadEvent` | [TUDPReadEvent](../types/TUDPReadEvent.md) | `__property TUDPReadEvent OnUDPRead;` |
| `OnUDPException: TIdUDPExceptionEvent` | [TIdUDPExceptionEvent](../types/TIdUDPExceptionEvent.md) | `__property TIdUDPExceptionEvent OnUDPException;` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
procedure Broadcast(const AData: string; const APort: TIdPort; const AIP: String = ''; AByteEncoding: IIdTextEncoding = nil ; ASrcEncoding: IIdTextEncoding = nil );
function ReceiveBuffer(var ABuffer : TIdBytes; var VPeerIP: string; var VPeerPort: TIdPort; AMSec: Integer = IdTimeoutDefault): integer;
function ReceiveString(const AMSec: Integer = IdTimeoutDefault; AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): string;
procedure Send(const AHost: string; const APort: TIdPort; const AData: string; AByteEncoding: IIdTextEncoding = nil ; ASrcEncoding: IIdTextEncoding = nil );
procedure SendBuffer(const AHost: string; const APort: TIdPort; const AIPVersion: TIdIPVersion; const ABuffer : TIdBytes);
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Broadcast(const UnicodeString AData, const TIdPort * APort, const UnicodeString AIP = '', IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ASrcEncoding = nil);
int __fastcall ReceiveBuffer(TIdBytes * &ABuffer, UnicodeString &VPeerIP, TIdPort * &VPeerPort, int AMSec = IdTimeoutDefault);
UnicodeString __fastcall ReceiveString(const int AMSec = IdTimeoutDefault, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ADestEncoding = nil);
void __fastcall Send(const UnicodeString AHost, const TIdPort * APort, const UnicodeString AData, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ASrcEncoding = nil);
void __fastcall SendBuffer(const UnicodeString AHost, const TIdPort * APort, const TIdIPVersion * AIPVersion, const TIdBytes * ABuffer);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

