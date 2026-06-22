# TsgcUDPServer

unit: sgcP2P
Edition: Professional

Add `sgcP2P` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `Host: String` | `String` | `__property UnicodeString Host;` |
| `Port: Integer` | `Integer` | `__property int Port;` |
| `IPVersion: TIdIPVersion` | `TIdIPVersion` | `__property TIdIPVersion * IPVersion;` |
| `Bindings: TIdSocketHandles` | [TIdSocketHandles](../types/TIdSocketHandles.md) | `__property TIdSocketHandles * Bindings;` |
| `LogFile: TsgcUDPLogFile` | [TsgcUDPLogFile](../types/TsgcUDPLogFile.md) | `__property TsgcUDPLogFile * LogFile;` |
| `NotifyEvents: TwsNotifyEvent` | [TwsNotifyEvent](../types/TwsNotifyEvent.md) | `__property TwsNotifyEvent NotifyEvents;` |
| `WatchDog: TsgcUDPWatchDogServer_Options` | [TsgcUDPWatchDogServer_Options](../types/TsgcUDPWatchDogServer_Options.md) | `__property TsgcUDPWatchDogServer_Options * WatchDog;` |
| `DTLS: Boolean` | `Boolean` | `__property bool DTLS;` |
| `DTLSOptions: TsgcUDPDTLS_Options` | [TsgcUDPDTLS_Options](../types/TsgcUDPDTLS_Options.md) | `__property TsgcUDPDTLS_Options * DTLSOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `UseNagle: Boolean` | `Boolean` | `__property bool UseNagle;` |
| `ConnectTimeout: Integer` | `Integer` | `__property int ConnectTimeout;` |
| `WriteTimeout: Integer` | `Integer` | `__property int WriteTimeout;` |
| `ReadTimeout: Integer` | `Integer` | `__property int ReadTimeout;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnStartup: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnStartup;` |
| `OnShutdown: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnShutdown;` |
| `OnUDPRead: TUDPReadEvent` | [TUDPReadEvent](../types/TUDPReadEvent.md) | `__property TUDPReadEvent OnUDPRead;` |
| `OnUDPException: TIdUDPExceptionEvent` | [TIdUDPExceptionEvent](../types/TIdUDPExceptionEvent.md) | `__property TIdUDPExceptionEvent OnUDPException;` |
| `OnBeforeWatchDog: TsgcUDPOnBeforeWatchDogEvent` | [TsgcUDPOnBeforeWatchDogEvent](../types/TsgcUDPOnBeforeWatchDogEvent.md) | `__property TsgcUDPOnBeforeWatchDogEvent OnBeforeWatchDog;` |
| `OnDTLSVerifyPeer: TsgcUDPDTLSVerifyPeerEvent` | [TsgcUDPDTLSVerifyPeerEvent](../types/TsgcUDPDTLSVerifyPeerEvent.md) | `__property TsgcUDPDTLSVerifyPeerEvent OnDTLSVerifyPeer;` |

## Methods

Delphi

```pascal
procedure ClearDTLS;
function AddBinding(const aIPAddress: string; aPort: Integer; const aName: string = ''): TIdSocketHandle;
function RemoveBinding(const aIPAddress: string; aPort: Integer): Boolean;
function GetBinding(const aIPAddress: string; aPort: Integer) : TIdSocketHandle;
procedure Start;
procedure Stop;
procedure ReStart;
procedure WriteData(const aIP: string; aPort: Word; const aValue: string);
procedure EnterCS;
procedure LeaveCS;
```

C++Builder

```cpp
void __fastcall ClearDTLS();
TIdSocketHandle * __fastcall AddBinding(const UnicodeString aIPAddress, int aPort, const UnicodeString aName = '');
bool __fastcall RemoveBinding(const UnicodeString aIPAddress, int aPort);
TIdSocketHandle * __fastcall GetBinding(const UnicodeString aIPAddress, int aPort);
void __fastcall Start();
void __fastcall Stop();
void __fastcall ReStart();
void __fastcall WriteData(const UnicodeString aIP, unsigned short aPort, const UnicodeString aValue);
void __fastcall EnterCS();
void __fastcall LeaveCS();
```

