# TIdSocksInfo

unit: IdSocks

Add `IdSocks` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Authentication: TSocksAuthentication` | [TSocksAuthentication](../types/TSocksAuthentication.md) | `__property TSocksAuthentication * Authentication;` |
| `Host: String` | `String` | `__property UnicodeString Host;` |
| `Password: String` | `String` | `__property UnicodeString Password;` |
| `Port: TIdPort` | `TIdPort` | `__property TIdPort * Port;` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](../types/TIdIPVersion.md) | `__property TIdIPVersion * IPVersion;` |
| `Username: String` | `String` | `__property UnicodeString Username;` |
| `Version: TSocksVersion` | [TSocksVersion](../types/TSocksVersion.md) | `__property TSocksVersion * Version;` |
| `ChainedProxy: TIdCustomTransparentProxy` | [TIdCustomTransparentProxy](../types/TIdCustomTransparentProxy.md) | `__property TIdCustomTransparentProxy * ChainedProxy;` |
| `Enabled: Boolean` | `Boolean` | `__property bool Enabled;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
procedure Assign(ASource: TPersistent);
procedure Bind(AIOHandler: TIdIOHandler; const AHost: string; const APort: TIdPort; const AIPVersion: TIdIPVersion = ID_DEFAULT_IP_VERSION);
function Listen(AIOHandler: TIdIOHandler; const ATimeOut:integer):boolean;
procedure OpenUDP(AHandle : TIdSocketHandle; const AHost: string = ''; const APort: TIdPort = 0; const AIPVersion: TIdIPVersion = ID_DEFAULT_IP_VERSION);
function RecvFromUDP(AHandle: TIdSocketHandle; var ABuffer : TIdBytes; var VPeerIP: string; var VPeerPort: TIdPort; var VIPVersion: TIdIPVersion; AMSec: Integer = IdTimeoutDefault): Integer;
procedure SendToUDP(AHandle: TIdSocketHandle; const AHost: string; const APort: TIdPort; const AIPVersion: TIdIPVersion; const ABuffer : TIdBytes);
procedure CloseUDP(AHandle: TIdSocketHandle);
procedure Connect(AIOHandler: TIdIOHandler; const AHost: string; const APort: TIdPort; const AIPVersion: TIdIPVersion = ID_DEFAULT_IP_VERSION);
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Assign(TPersistent * ASource);
void __fastcall Bind(TIdIOHandler * AIOHandler, const UnicodeString AHost, const TIdPort * APort, const TIdIPVersion * AIPVersion = ID_DEFAULT_IP_VERSION);
bool __fastcall Listen(TIdIOHandler * AIOHandler, const int ATimeOut);
void __fastcall OpenUDP(TIdSocketHandle * AHandle, const UnicodeString AHost = '', const TIdPort * APort = 0, const TIdIPVersion * AIPVersion = ID_DEFAULT_IP_VERSION);
int __fastcall RecvFromUDP(TIdSocketHandle * AHandle, TIdBytes * &ABuffer, UnicodeString &VPeerIP, TIdPort * &VPeerPort, TIdIPVersion * &VIPVersion, int AMSec = IdTimeoutDefault);
void __fastcall SendToUDP(TIdSocketHandle * AHandle, const UnicodeString AHost, const TIdPort * APort, const TIdIPVersion * AIPVersion, const TIdBytes * ABuffer);
void __fastcall CloseUDP(TIdSocketHandle * AHandle);
void __fastcall Connect(TIdIOHandler * AIOHandler, const UnicodeString AHost, const TIdPort * APort, const TIdIPVersion * AIPVersion = ID_DEFAULT_IP_VERSION);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

