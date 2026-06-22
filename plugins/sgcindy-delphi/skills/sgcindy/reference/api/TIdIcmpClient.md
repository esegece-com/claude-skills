# TIdIcmpClient

unit: IdIcmpClient

Add `IdIcmpClient` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `ReplyData: string (read-only)` | `string` | `__property UnicodeString ReplyData /* read-only */;` |
| `ReplyStatus: TReplyStatus (read-only)` | [TReplyStatus](../types/TReplyStatus.md) | `__property TReplyStatus * ReplyStatus /* read-only */;` |
| `Host: string` | `string` | `__property UnicodeString Host;` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](../types/TIdIPVersion.md) | `__property TIdIPVersion * IPVersion;` |
| `PacketSize: Integer` | `Integer` | `__property int PacketSize;` |
| `ReceiveTimeout: integer` | `integer` | `__property int ReceiveTimeout;` |
| `Port: TIdPort` | `TIdPort` | `__property TIdPort * Port;` |
| `Protocol: TIdSocketProtocol` | `TIdSocketProtocol` | `__property TIdSocketProtocol * Protocol;` |
| `ProtocolIPv6: TIdSocketProtocol` | `TIdSocketProtocol` | `__property TIdSocketProtocol * ProtocolIPv6;` |
| `Binding: TIdSocketHandle (read-only)` | [TIdSocketHandle](../types/TIdSocketHandle.md) | `__property TIdSocketHandle * Binding /* read-only */;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnReply: TOnReplyEvent` | [TOnReplyEvent](../types/TOnReplyEvent.md) | `__property TOnReplyEvent OnReply;` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
procedure Ping(const ABuffer: TIdBytes = nil; SequenceID: Word = 0);
procedure Send(const AHost: string; const APort: TIdPort; const ABuffer : TIdBytes);
function Receive(ATimeOut: Integer): TReplyStatus;
function ReceiveBuffer(var VBuffer : TIdBytes; ATimeOut: Integer = -1): Integer;
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Ping(const TIdBytes * ABuffer = nil, unsigned short SequenceID = 0);
void __fastcall Send(const UnicodeString AHost, const TIdPort * APort, const TIdBytes * ABuffer);
TReplyStatus * __fastcall Receive(int ATimeOut);
int __fastcall ReceiveBuffer(TIdBytes * &VBuffer, int ATimeOut = -1);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

