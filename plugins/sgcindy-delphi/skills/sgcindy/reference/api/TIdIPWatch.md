# TIdIPWatch

unit: IdIPWatch

Add `IdIPWatch` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `CurrentIP: string (read-only)` | `string` | `__property UnicodeString CurrentIP /* read-only */;` |
| `IPHistoryList: TStringList (read-only)` | `TStringList` | `__property TStringList * IPHistoryList /* read-only */;` |
| `IsOnline: Boolean (read-only)` | `Boolean` | `__property bool IsOnline /* read-only */;` |
| `PreviousIP: string (read-only)` | `string` | `__property UnicodeString PreviousIP /* read-only */;` |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `HistoryEnabled: Boolean` | `Boolean` | `__property bool HistoryEnabled;` |
| `HistoryFilename: string` | `string` | `__property UnicodeString HistoryFilename;` |
| `MaxHistoryEntries: Integer` | `Integer` | `__property int MaxHistoryEntries;` |
| `WatchInterval: UInt32` | `UInt32` | `__property UInt32 WatchInterval;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnStatusChanged: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnStatusChanged;` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
function ForceCheck: Boolean;
procedure LoadHistory;
function LocalIP: string;
procedure SaveHistory;
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
bool __fastcall ForceCheck();
void __fastcall LoadHistory();
UnicodeString __fastcall LocalIP();
void __fastcall SaveHistory();
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

