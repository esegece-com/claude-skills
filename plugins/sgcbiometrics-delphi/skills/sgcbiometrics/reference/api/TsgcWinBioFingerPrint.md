# TsgcWinBioFingerPrint

unit: sgcBiometrics

Add `sgcBiometrics` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Storage: TsgcBiometrics_WinBio_Storage` | [TsgcBiometrics_WinBio_Storage](../types/TsgcBiometrics_WinBio_Storage.md) | `__property TsgcBiometrics_WinBio_Storage * Storage;` |
| `Users: TsgcBiometrics_WinBio_Users` | [TsgcBiometrics_WinBio_Users](../types/TsgcBiometrics_WinBio_Users.md) | `__property TsgcBiometrics_WinBio_Users * Users;` |
| `Asynchronous: Boolean` | `Boolean` | `__property bool Asynchronous;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `RunsAsConsole: Boolean` | `Boolean` | `__property bool RunsAsConsole;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnOpenSession: TsgcWinBioOpenSessionEvent` | [TsgcWinBioOpenSessionEvent](../types/TsgcWinBioOpenSessionEvent.md) | `__property TsgcWinBioOpenSessionEvent OnOpenSession;` |
| `OnCloseSession: TsgcWinBioCloseSessionEvent` | [TsgcWinBioCloseSessionEvent](../types/TsgcWinBioCloseSessionEvent.md) | `__property TsgcWinBioCloseSessionEvent OnCloseSession;` |
| `OnCancel: TsgcWinBioCancelEvent` | [TsgcWinBioCancelEvent](../types/TsgcWinBioCancelEvent.md) | `__property TsgcWinBioCancelEvent OnCancel;` |
| `OnSensorLocated: TsgcWinBioLocateSensorEvent` | [TsgcWinBioLocateSensorEvent](../types/TsgcWinBioLocateSensorEvent.md) | `__property TsgcWinBioLocateSensorEvent OnSensorLocated;` |
| `OnIdentify: TsgcWinBioIdentifyEvent` | [TsgcWinBioIdentifyEvent](../types/TsgcWinBioIdentifyEvent.md) | `__property TsgcWinBioIdentifyEvent OnIdentify;` |
| `OnVerify: TsgcWinBioVerifyEvent` | [TsgcWinBioVerifyEvent](../types/TsgcWinBioVerifyEvent.md) | `__property TsgcWinBioVerifyEvent OnVerify;` |
| `OnCaptureSample: TsgcWinBioCaptureSampleEvent` | [TsgcWinBioCaptureSampleEvent](../types/TsgcWinBioCaptureSampleEvent.md) | `__property TsgcWinBioCaptureSampleEvent OnCaptureSample;` |
| `OnCaptureSampleReject: TsgcWinBioCaptureSampleRejectEvent` | [TsgcWinBioCaptureSampleRejectEvent](../types/TsgcWinBioCaptureSampleRejectEvent.md) | `__property TsgcWinBioCaptureSampleRejectEvent OnCaptureSampleReject;` |
| `OnEnumBiometricUnit: TsgcWinBioEnumBiometricUnitEvent` | [TsgcWinBioEnumBiometricUnitEvent](../types/TsgcWinBioEnumBiometricUnitEvent.md) | `__property TsgcWinBioEnumBiometricUnitEvent OnEnumBiometricUnit;` |
| `OnEnumDatabase: TsgcWinBioEnumDatabaseEvent` | [TsgcWinBioEnumDatabaseEvent](../types/TsgcWinBioEnumDatabaseEvent.md) | `__property TsgcWinBioEnumDatabaseEvent OnEnumDatabase;` |
| `OnEnumEnrollments: TsgcWinBioEnumEnrollmentsEvent` | [TsgcWinBioEnumEnrollmentsEvent](../types/TsgcWinBioEnumEnrollmentsEvent.md) | `__property TsgcWinBioEnumEnrollmentsEvent OnEnumEnrollments;` |
| `OnEnrollBegin: TsgcWinBioEnrollBeginEvent` | [TsgcWinBioEnrollBeginEvent](../types/TsgcWinBioEnrollBeginEvent.md) | `__property TsgcWinBioEnrollBeginEvent OnEnrollBegin;` |
| `OnEnrollCapture: TsgcWinBioEnrollCaptureEvent` | [TsgcWinBioEnrollCaptureEvent](../types/TsgcWinBioEnrollCaptureEvent.md) | `__property TsgcWinBioEnrollCaptureEvent OnEnrollCapture;` |
| `OnEnrollCommit: TsgcWinBioEnrollCommitEvent` | [TsgcWinBioEnrollCommitEvent](../types/TsgcWinBioEnrollCommitEvent.md) | `__property TsgcWinBioEnrollCommitEvent OnEnrollCommit;` |
| `OnBeforeInitializeStorage: TsgcWinBioBeforeInitializeStorage` | [TsgcWinBioBeforeInitializeStorage](../types/TsgcWinBioBeforeInitializeStorage.md) | `__property TsgcWinBioBeforeInitializeStorage * OnBeforeInitializeStorage;` |
| `OnAfterInitializeStorage: TsgcWinBioAfterInitializeStorage` | [TsgcWinBioAfterInitializeStorage](../types/TsgcWinBioAfterInitializeStorage.md) | `__property TsgcWinBioAfterInitializeStorage * OnAfterInitializeStorage;` |
| `OnTemplateDeleted: TsgcWinBioTemplateDeleted` | [TsgcWinBioTemplateDeleted](../types/TsgcWinBioTemplateDeleted.md) | `__property TsgcWinBioTemplateDeleted * OnTemplateDeleted;` |
| `OnError: TsgcWinBioErrorEvent` | [TsgcWinBioErrorEvent](../types/TsgcWinBioErrorEvent.md) | `__property TsgcWinBioErrorEvent OnError;` |

## Methods

Delphi

```pascal
procedure Identify;
procedure DeleteTemplate(const aIdentity: WINBIO_IDENTITY; const aSubFactor: WINBIO_BIOMETRIC_SUBTYPE);
procedure CaptureSample(const aPurpose : WINBIO_BIR_PURPOSE = WINBIO_NO_PURPOSE_AVAILABLE; const aFlags: WINBIO_BIR_DATA_FLAGS = WINBIO_DATA_FLAG_RAW);
procedure EnrollBiometric(aSubType : WINBIO_BIOMETRIC_SUBTYPE = WINBIO_SUBTYPE_NO_INFORMATION);
procedure EnumBiometricUnits;
procedure EnumDatabases;
procedure LocateSensor;
procedure RebuildStorage;
procedure VerifyIdentity(const aIdentity: WINBIO_IDENTITY; const aSubFactor: WINBIO_BIOMETRIC_SUBTYPE);
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
void __fastcall Identify();
void __fastcall DeleteTemplate(const WINBIO_IDENTITY aIdentity, const WINBIO_BIOMETRIC_SUBTYPE aSubFactor);
void __fastcall CaptureSample(const WINBIO_BIR_PURPOSE aPurpose = WINBIO_NO_PURPOSE_AVAILABLE, const WINBIO_BIR_DATA_FLAGS aFlags = WINBIO_DATA_FLAG_RAW);
void __fastcall EnrollBiometric(WINBIO_BIOMETRIC_SUBTYPE aSubType = WINBIO_SUBTYPE_NO_INFORMATION);
void __fastcall EnumBiometricUnits();
void __fastcall EnumDatabases();
void __fastcall LocateSensor();
void __fastcall RebuildStorage();
void __fastcall VerifyIdentity(const WINBIO_IDENTITY aIdentity, const WINBIO_BIOMETRIC_SUBTYPE aSubFactor);
void __fastcall DoSyncOpenSession();
void __fastcall DoAsyncOpenSession();
bool __fastcall SessionIsOpen();
void __fastcall Cancel();
void __fastcall CloseSession();
void __fastcall EnumEnrollments();
bool __fastcall InitializeSensors();
```

