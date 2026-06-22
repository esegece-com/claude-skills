# TIdSysLog

unit: IdSysLog

Add `IdSysLog` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Port: TIdPort` | `TIdPort` | `__property TIdPort * Port;` |
| `BoundIP: string` | `string` | `__property UnicodeString BoundIP;` |
| `BoundPort: TIdPort` | `TIdPort` | `__property TIdPort * BoundPort;` |
| `BoundPortMin: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMin;` |
| `BoundPortMax: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMax;` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](../types/TIdIPVersion.md) | `__property TIdIPVersion * IPVersion;` |
| `Host: String` | `String` | `__property UnicodeString Host;` |
| `ReceiveTimeout: Integer` | `Integer` | `__property int ReceiveTimeout;` |
| `ReuseSocket: TIdReuseSocket` | [TIdReuseSocket](../types/TIdReuseSocket.md) | `__property TIdReuseSocket * ReuseSocket;` |
| `TransparentProxy: TIdCustomTransparentProxy` | [TIdCustomTransparentProxy](../types/TIdCustomTransparentProxy.md) | `__property TIdCustomTransparentProxy * TransparentProxy;` |
| `Binding: TIdSocketHandle (read-only)` | [TIdSocketHandle](../types/TIdSocketHandle.md) | `__property TIdSocketHandle * Binding /* read-only */;` |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `BufferSize: Integer` | `Integer` | `__property int BufferSize;` |
| `BroadcastEnabled: Boolean` | `Boolean` | `__property bool BroadcastEnabled;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnected: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnConnected;` |
| `OnDisconnected: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDisconnected;` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
procedure SendLogMessage(const AMsg: TIdSysLogMessage; const AAutoTimeStamp: Boolean = true);
procedure OpenProxy;
procedure CloseProxy;
procedure Connect;
procedure Disconnect;
function Connected: Boolean;
function ReceiveBuffer(var ABuffer : TIdBytes; const AMSec: Integer = IdTimeoutDefault): Integer;
procedure Send(const AData: string; AByteEncoding: IIdTextEncoding = nil ; ASrcEncoding: IIdTextEncoding = nil );
procedure SendBuffer(const AHost: string; const APort: TIdPort; const ABuffer : TIdBytes);
procedure Broadcast(const AData: string; const APort: TIdPort; const AIP: String = ''; AByteEncoding: IIdTextEncoding = nil ; ASrcEncoding: IIdTextEncoding = nil );
function ReceiveString(const AMSec: Integer = IdTimeoutDefault; AByteEncoding: IIdTextEncoding = nil ; ADestEncoding: IIdTextEncoding = nil ): string;
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall SendLogMessage(const TIdSysLogMessage * AMsg, const bool AAutoTimeStamp = true);
void __fastcall OpenProxy();
void __fastcall CloseProxy();
void __fastcall Connect();
void __fastcall Disconnect();
bool __fastcall Connected();
int __fastcall ReceiveBuffer(TIdBytes * &ABuffer, const int AMSec = IdTimeoutDefault);
void __fastcall Send(const UnicodeString AData, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ASrcEncoding = nil);
void __fastcall SendBuffer(const UnicodeString AHost, const TIdPort * APort, const TIdBytes * ABuffer);
void __fastcall Broadcast(const UnicodeString AData, const TIdPort * APort, const UnicodeString AIP = '', IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ASrcEncoding = nil);
UnicodeString __fastcall ReceiveString(const int AMSec = IdTimeoutDefault, IIdTextEncoding AByteEncoding = nil, IIdTextEncoding ADestEncoding = nil);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

