# TsgcWinBioFacial

unit: sgcBiometrics

Add `sgcBiometrics` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `RunsAsConsole: Boolean` | `Boolean` | `__property bool RunsAsConsole;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnOpenSession: TsgcWinBioOpenSessionEvent` | [TsgcWinBioOpenSessionEvent](../types/TsgcWinBioOpenSessionEvent.md) | `__property TsgcWinBioOpenSessionEvent OnOpenSession;` |
| `OnCloseSession: TsgcWinBioCloseSessionEvent` | [TsgcWinBioCloseSessionEvent](../types/TsgcWinBioCloseSessionEvent.md) | `__property TsgcWinBioCloseSessionEvent OnCloseSession;` |
| `OnCancel: TsgcWinBioCancelEvent` | [TsgcWinBioCancelEvent](../types/TsgcWinBioCancelEvent.md) | `__property TsgcWinBioCancelEvent OnCancel;` |
| `OnEnumBiometricUnit: TsgcWinBioEnumBiometricUnitEvent` | [TsgcWinBioEnumBiometricUnitEvent](../types/TsgcWinBioEnumBiometricUnitEvent.md) | `__property TsgcWinBioEnumBiometricUnitEvent OnEnumBiometricUnit;` |
| `OnEnumEnrollments: TsgcWinBioEnumEnrollmentsEvent` | [TsgcWinBioEnumEnrollmentsEvent](../types/TsgcWinBioEnumEnrollmentsEvent.md) | `__property TsgcWinBioEnumEnrollmentsEvent OnEnumEnrollments;` |
| `OnError: TsgcWinBioErrorEvent` | [TsgcWinBioErrorEvent](../types/TsgcWinBioErrorEvent.md) | `__property TsgcWinBioErrorEvent OnError;` |
| `OnPresenceArrive: TsgcWinBioPresenceArrive` | [TsgcWinBioPresenceArrive](../types/TsgcWinBioPresenceArrive.md) | `__property TsgcWinBioPresenceArrive * OnPresenceArrive;` |
| `OnPresenceDepart: TsgcWinBioPresenceDepart` | [TsgcWinBioPresenceDepart](../types/TsgcWinBioPresenceDepart.md) | `__property TsgcWinBioPresenceDepart * OnPresenceDepart;` |
| `OnPresenceRecognize: TsgcWinBioPresenceRecognize` | [TsgcWinBioPresenceRecognize](../types/TsgcWinBioPresenceRecognize.md) | `__property TsgcWinBioPresenceRecognize * OnPresenceRecognize;` |
| `OnPresenceTrack: TsgcWinBioPresenceTrack` | [TsgcWinBioPresenceTrack](../types/TsgcWinBioPresenceTrack.md) | `__property TsgcWinBioPresenceTrack * OnPresenceTrack;` |
| `OnPresenceUpdateAll: TsgcWinBioPresenceUpdateAll` | [TsgcWinBioPresenceUpdateAll](../types/TsgcWinBioPresenceUpdateAll.md) | `__property TsgcWinBioPresenceUpdateAll * OnPresenceUpdateAll;` |
| `OnPresenceUnknown: TsgcWinBioPresenceUnknown` | [TsgcWinBioPresenceUnknown](../types/TsgcWinBioPresenceUnknown.md) | `__property TsgcWinBioPresenceUnknown * OnPresenceUnknown;` |

## Methods

Delphi

```pascal
procedure StartMonitorPresence(const aTimeout: Integer = 10000);
procedure StopMonitorPresence;
function FacialRecognize(const aAccountSid: String = ''; const aTimeout: Integer = 10000): Boolean;
function FacialIdentify(const aTimeout: Integer = 10000): String;
procedure DoSyncOpenSession;
procedure DoAsyncOpenSession;
function SessionIsOpen: Boolean;
procedure Cancel;
procedure CloseSession;
procedure EnumEnrollments;
function InitializeSensors: Boolean;
```

C++Builder

```cpp
void __fastcall StartMonitorPresence(const int aTimeout = 10000);
void __fastcall StopMonitorPresence();
bool __fastcall FacialRecognize(const UnicodeString aAccountSid = '', const int aTimeout = 10000);
UnicodeString __fastcall FacialIdentify(const int aTimeout = 10000);
void __fastcall DoSyncOpenSession();
void __fastcall DoAsyncOpenSession();
bool __fastcall SessionIsOpen();
void __fastcall Cancel();
void __fastcall CloseSession();
void __fastcall EnumEnrollments();
bool __fastcall InitializeSensors();
```

