# TIdSocketHandle

kind: class
unit: IdSocketHandle

## Properties

| Delphi | Type |
| --- | --- |
| `Name: string` | `string` |
| `IO: Boolean` | `Boolean` |
| `HandleAllocated: Boolean (read-only)` | `Boolean` |
| `Handle: TIdStackSocketHandle (read-only)` | `TIdStackSocketHandle` |
| `OverLapped: Boolean` | `Boolean` |
| `PeerIP: string (read-only)` | `string` |
| `PeerPort: TIdPort (read-only)` | `TIdPort` |
| `SocketType: TIdSocketType (read-only)` | `TIdSocketType` |
| `BroadcastEnabled: Boolean` | `Boolean` |
| `ClientPortMin: TIdPort` | `TIdPort` |
| `ClientPortMax: TIdPort` | `TIdPort` |
| `IP: string` | `string` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](./TIdIPVersion.md) |
| `LingerState: Integer` | `Integer` |
| `Port: TIdPort` | `TIdPort` |
| `ReuseSocket: TIdReuseSocket` | [TIdReuseSocket](./TIdReuseSocket.md) |
| `UseNagle: Boolean` | `Boolean` |

## Methods

```pascal
function Accept(ASocket: TIdStackSocketHandle): Boolean;
procedure AllocateSocket(const ASocketType: TIdSocketType = Id_SOCK_STREAM; const AProtocol: TIdSocketProtocol = Id_IPPROTO_IP);
procedure Assign(Source: TPersistent);
procedure Bind;
procedure Broadcast(const AData: string; const APort: TIdPort; const AIP: String = ''; AByteEncoding: IIdTextEncoding = nil ; ASrcEncoding: IIdTextEncoding = nil );
procedure CloseSocket;
procedure Connect;
procedure Listen(const AQueueCount: Integer = 5);
function Readable(AMSec: Integer = IdTimeoutDefault): boolean;
function Receive(var VBuffer: TIdBytes): Integer;
function RecvFrom(var ABuffer : TIdBytes; var VIP: string; var VPort: TIdPort; var VIPVersion: TIdIPVersion): Integer;
procedure Reset(const AResetLocal: boolean = True);
function Send(const AData: String; AByteEncoding: IIdTextEncoding = nil ; ASrcEncoding: IIdTextEncoding = nil ): Integer;
procedure SendTo(const AIP: string; const APort: TIdPort; const AData: String; const AIPVersion: TIdIPVersion = ID_DEFAULT_IP_VERSION; AByteEncoding: IIdTextEncoding = nil ; ASrcEncoding: IIdTextEncoding = nil );
procedure SetPeer(const AIP: string; const APort: TIdPort; const AIPVersion : TIdIPVersion = ID_DEFAULT_IP_VERSION);
procedure SetBinding(const AIP: string; const APort: TIdPort; const AIPVersion : TIdIPVersion = ID_DEFAULT_IP_VERSION);
procedure GetSockOpt(ALevel: TIdSocketOptionLevel; AOptName: TIdSocketOption; out VOptVal: Integer);
procedure SetSockOpt(ALevel: TIdSocketOptionLevel; AOptName: TIdSocketOption; AOptVal: Integer);
function Select(ATimeout: Integer = IdTimeoutInfinite): Boolean;
procedure UpdateBindingLocal;
procedure UpdateBindingPeer;
procedure AddMulticastMembership(const AGroupIP: String);
procedure DropMulticastMembership(const AGroupIP: String);
procedure SetKeepAliveValues(const AEnabled: Boolean; const ATimeMS, AInterval: Integer);
procedure SetLoopBack(const AValue: Boolean);
procedure SetMulticastTTL(const AValue: Byte);
procedure SetTTL(const AValue: Integer);
procedure SetNagleOpt(const AEnabled: Boolean);
```

