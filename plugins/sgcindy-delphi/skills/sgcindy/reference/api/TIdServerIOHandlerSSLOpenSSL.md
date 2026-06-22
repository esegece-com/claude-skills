# TIdServerIOHandlerSSLOpenSSL

unit: IdSSLOpenSSL

Add `IdSSLOpenSSL` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `SSLContext: TIdSSLContext (read-only)` | [TIdSSLContext](../types/TIdSSLContext.md) | `__property TIdSSLContext * SSLContext /* read-only */;` |
| `SSLOptions: TIdSSLOptions` | [TIdSSLOptions](../types/TIdSSLOptions.md) | `__property TIdSSLOptions * SSLOptions;` |
| `IO: Boolean` | `Boolean` | `__property bool IO;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnStatusInfo: TCallbackEvent` | [TCallbackEvent](../types/TCallbackEvent.md) | `__property TCallbackEvent OnStatusInfo;` |
| `OnStatusInfoEx: TCallbackExEvent` | [TCallbackExEvent](../types/TCallbackExEvent.md) | `__property TCallbackExEvent OnStatusInfoEx;` |
| `OnGetPassword: TPasswordEvent` | [TPasswordEvent](../types/TPasswordEvent.md) | `__property TPasswordEvent OnGetPassword;` |
| `OnGetPasswordEx: TPasswordEventEx` | [TPasswordEventEx](../types/TPasswordEventEx.md) | `__property TPasswordEventEx * OnGetPasswordEx;` |
| `OnVerifyPeer: TVerifyPeerEvent` | [TVerifyPeerEvent](../types/TVerifyPeerEvent.md) | `__property TVerifyPeerEvent OnVerifyPeer;` |
| `OnALPNSelect: TALPNSelectEvent` | [TALPNSelectEvent](../types/TALPNSelectEvent.md) | `__property TALPNSelectEvent OnALPNSelect;` |
| `OnSocketAccept: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnSocketAccept;` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
procedure Init;
procedure Shutdown;
function Accept(ASocket: TIdSocketHandle; AListenerThread: TIdThread; AYarn: TIdYarn): TIdIOHandler;
function MakeClientIOHandler: TIdSSLIOHandlerSocketBase;
function MakeFTPSvrPort: TIdSSLIOHandlerSocketBase;
function MakeFTPSvrPasv: TIdSSLIOHandlerSocketBase;
procedure Listen(ASocket: TIdSocketHandle);
procedure StopListening;
procedure SetServer(const aValue: TObject);
procedure SetScheduler(AScheduler: TIdScheduler);
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Init();
void __fastcall Shutdown();
TIdIOHandler * __fastcall Accept(TIdSocketHandle * ASocket, TIdThread * AListenerThread, TIdYarn * AYarn);
TIdSSLIOHandlerSocketBase * __fastcall MakeClientIOHandler();
TIdSSLIOHandlerSocketBase * __fastcall MakeFTPSvrPort();
TIdSSLIOHandlerSocketBase * __fastcall MakeFTPSvrPasv();
void __fastcall Listen(TIdSocketHandle * ASocket);
void __fastcall StopListening();
void __fastcall SetServer(const TObject * aValue);
void __fastcall SetScheduler(TIdScheduler * AScheduler);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

