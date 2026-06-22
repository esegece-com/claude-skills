# TIdCustomTransparentProxy

kind: class
unit: IdCustomTransparentProxy

## Properties

| Delphi | Type |
| --- | --- |
| `Enabled: Boolean` | `Boolean` |
| `Host: String` | `String` |
| `Password: String` | `String` |
| `Port: TIdPort` | `TIdPort` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](./TIdIPVersion.md) |
| `Username: String` | `String` |
| `ChainedProxy: TIdCustomTransparentProxy` | [TIdCustomTransparentProxy](./TIdCustomTransparentProxy.md) |
| `WorkTarget: TIdComponent` | [TIdComponent](./TIdComponent.md) |
| `Version: string (read-only)` | `string` |

## Events

| Delphi | Type |
| --- | --- |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](./TIdStatusEvent.md) |

## Methods

```pascal
procedure Assign(ASource: TPersistent);
procedure OpenUDP(AHandle : TIdSocketHandle; const AHost: string = ''; const APort: TIdPort = 0; const AIPVersion: TIdIPVersion = ID_DEFAULT_IP_VERSION);
procedure CloseUDP(AHandle: TIdSocketHandle);
function RecvFromUDP(AHandle: TIdSocketHandle; var ABuffer : TIdBytes; var VPeerIP: string; var VPeerPort: TIdPort; var VIPVersion: TIdIPVersion; AMSec: Integer = IdTimeoutDefault): Integer;
procedure SendToUDP(AHandle: TIdSocketHandle; const AHost: string; const APort: TIdPort; const AIPVersion: TIdIPVersion; const ABuffer : TIdBytes);
procedure Connect(AIOHandler: TIdIOHandler; const AHost: string; const APort: TIdPort; const AIPVersion: TIdIPVersion = ID_DEFAULT_IP_VERSION);
procedure Bind(AIOHandler: TIdIOHandler; const AHost: string; const APort: TIdPort; const AIPVersion: TIdIPVersion = ID_DEFAULT_IP_VERSION);
function Listen(AIOHandler: TIdIOHandler; const ATimeOut: Integer): Boolean;
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

