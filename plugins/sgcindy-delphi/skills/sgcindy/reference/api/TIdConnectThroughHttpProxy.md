# TIdConnectThroughHttpProxy

unit: IdConnectThroughHttpProxy

Add `IdConnectThroughHttpProxy` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Enabled: Boolean` | `Boolean` | `__property bool Enabled;` |
| `Host: String` | `String` | `__property UnicodeString Host;` |
| `Port: TIdPort` | `TIdPort` | `__property TIdPort * Port;` |
| `ChainedProxy: TIdCustomTransparentProxy` | [TIdCustomTransparentProxy](../types/TIdCustomTransparentProxy.md) | `__property TIdCustomTransparentProxy * ChainedProxy;` |
| `Username: String` | `String` | `__property UnicodeString Username;` |
| `Password: String` | `String` | `__property UnicodeString Password;` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](../types/TIdIPVersion.md) | `__property TIdIPVersion * IPVersion;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

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

C++Builder

```cpp
void __fastcall Assign(TPersistent * ASource);
void __fastcall OpenUDP(TIdSocketHandle * AHandle, const UnicodeString AHost = '', const TIdPort * APort = 0, const TIdIPVersion * AIPVersion = ID_DEFAULT_IP_VERSION);
void __fastcall CloseUDP(TIdSocketHandle * AHandle);
int __fastcall RecvFromUDP(TIdSocketHandle * AHandle, TIdBytes * &ABuffer, UnicodeString &VPeerIP, TIdPort * &VPeerPort, TIdIPVersion * &VIPVersion, int AMSec = IdTimeoutDefault);
void __fastcall SendToUDP(TIdSocketHandle * AHandle, const UnicodeString AHost, const TIdPort * APort, const TIdIPVersion * AIPVersion, const TIdBytes * ABuffer);
void __fastcall Connect(TIdIOHandler * AIOHandler, const UnicodeString AHost, const TIdPort * APort, const TIdIPVersion * AIPVersion = ID_DEFAULT_IP_VERSION);
void __fastcall Bind(TIdIOHandler * AIOHandler, const UnicodeString AHost, const TIdPort * APort, const TIdIPVersion * AIPVersion = ID_DEFAULT_IP_VERSION);
bool __fastcall Listen(TIdIOHandler * AIOHandler, const int ATimeOut);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

