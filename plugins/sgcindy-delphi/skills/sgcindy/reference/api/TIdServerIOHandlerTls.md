# TIdServerIOHandlerTls

unit: IdServerIOHandlerTls

Add `IdServerIOHandlerTls` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Options: TIdTlsServerOptions` | [TIdTlsServerOptions](../types/TIdTlsServerOptions.md) | `__property TIdTlsServerOptions * Options;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnSocketAccept: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnSocketAccept;` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
function MakeFTPSvrPasv: TIdSSLIOHandlerSocketBase;
function MakeFTPSvrPort: TIdSSLIOHandlerSocketBase;
function MakeClientIOHandler(AYarn: TIdYarn) : TIdIOHandler;
function Accept(ASocket: TIdSocketHandle; AListenerThread: TIdThread; AYarn: TIdYarn): TIdIOHandler;
procedure Listen(ASocket: TIdSocketHandle);
procedure StopListening;
procedure SetServer(const aValue: TObject);
procedure Init;
procedure Shutdown;
procedure SetScheduler(AScheduler: TIdScheduler);
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
TIdSSLIOHandlerSocketBase * __fastcall MakeFTPSvrPasv();
TIdSSLIOHandlerSocketBase * __fastcall MakeFTPSvrPort();
TIdIOHandler * __fastcall MakeClientIOHandler(TIdYarn * AYarn);
TIdIOHandler * __fastcall Accept(TIdSocketHandle * ASocket, TIdThread * AListenerThread, TIdYarn * AYarn);
void __fastcall Listen(TIdSocketHandle * ASocket);
void __fastcall StopListening();
void __fastcall SetServer(const TObject * aValue);
void __fastcall Init();
void __fastcall Shutdown();
void __fastcall SetScheduler(TIdScheduler * AScheduler);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

