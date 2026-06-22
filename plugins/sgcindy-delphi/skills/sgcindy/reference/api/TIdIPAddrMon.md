# TIdIPAddrMon

unit: IdIPAddrMon

Add `IdIPAddrMon` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `AdapterCount: Integer (read-only)` | `Integer` | `__property int AdapterCount /* read-only */;` |
| `Busy: Boolean (read-only)` | `Boolean` | `__property bool Busy /* read-only */;` |
| `IPAddresses: TStrings (read-only)` | `TStrings` | `__property TStrings * IPAddresses /* read-only */;` |
| `Thread: TIdIPAddrMonThread (read-only)` | [TIdIPAddrMonThread](../types/TIdIPAddrMonThread.md) | `__property TIdIPAddrMonThread * Thread /* read-only */;` |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `Interval: UInt32` | `UInt32` | `__property UInt32 Interval;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnStatusChanged: TIdIPAddrMonEvent` | [TIdIPAddrMonEvent](../types/TIdIPAddrMonEvent.md) | `__property TIdIPAddrMonEvent OnStatusChanged;` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
procedure CheckAdapters(Sender: TObject);
procedure ForceCheck;
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall CheckAdapters(TObject * Sender);
void __fastcall ForceCheck();
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

