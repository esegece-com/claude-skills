# TIdServerIOHandlerSSLNET

unit: IdSSLDotNET

Add `IdSSLDotNET` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `enabledSslProtocols: System.Security.Authentication.SslProtocols` | `SslProtocols` | `__property System.Security.Authentication.SslProtocols enabledSslProtocols;` |
| `ServerCertificate: X509Certificate` | `X509Certificate` | `__property X509Certificate ServerCertificate;` |
| `clientCertificateRequired: Boolean` | `Boolean` | `__property bool clientCertificateRequired;` |
| `checkCertificateRevocation: Boolean` | `Boolean` | `__property bool checkCertificateRevocation;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnSSLHandshakeDone: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnSSLHandshakeDone;` |
| `OnLocalCertificateSelection: TOnLocalCertificateSelectionCallback` | [TOnLocalCertificateSelectionCallback](../types/TOnLocalCertificateSelectionCallback.md) | `__property TOnLocalCertificateSelectionCallback OnLocalCertificateSelection;` |
| `OnValidatePeerCertificate: TOnValidatePeerCertificate` | [TOnValidatePeerCertificate](../types/TOnValidatePeerCertificate.md) | `__property TOnValidatePeerCertificate OnValidatePeerCertificate;` |
| `OnSocketAccept: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnSocketAccept;` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
procedure Init;
procedure Shutdown;
function MakeClientIOHandler : TIdSSLIOHandlerSocketBase;
function MakeFTPSvrPort : TIdSSLIOHandlerSocketBase;
function MakeFTPSvrPasv : TIdSSLIOHandlerSocketBase;
function Accept(ASocket: TIdSocketHandle; AListenerThread: TIdThread; AYarn: TIdYarn): TIdIOHandler;
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
TIdSSLIOHandlerSocketBase * __fastcall MakeClientIOHandler();
TIdSSLIOHandlerSocketBase * __fastcall MakeFTPSvrPort();
TIdSSLIOHandlerSocketBase * __fastcall MakeFTPSvrPasv();
TIdIOHandler * __fastcall Accept(TIdSocketHandle * ASocket, TIdThread * AListenerThread, TIdYarn * AYarn);
void __fastcall Listen(TIdSocketHandle * ASocket);
void __fastcall StopListening();
void __fastcall SetServer(const TObject * aValue);
void __fastcall SetScheduler(TIdScheduler * AScheduler);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

