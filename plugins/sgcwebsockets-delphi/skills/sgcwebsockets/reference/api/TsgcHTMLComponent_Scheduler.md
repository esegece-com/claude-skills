# TsgcHTMLComponent_Scheduler

unit: sgcHTML_Component_Scheduler
Edition: All-Access

Add `sgcHTML_Component_Scheduler` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Events: TsgcHTMLSchedulerEvents` | [TsgcHTMLSchedulerEvents](../types/TsgcHTMLSchedulerEvents.md) | `__property TsgcHTMLSchedulerEvents * Events;` |
| `View: TsgcHTMLSchedulerView` | [TsgcHTMLSchedulerView](../types/TsgcHTMLSchedulerView.md) | `__property TsgcHTMLSchedulerView * View;` |
| `CurrentDate: TDateTime` | `TDateTime` | `__property System::TDateTime CurrentDate;` |
| `SchedulerID: string` | `string` | `__property UnicodeString SchedulerID;` |
| `StartHour: Integer` | `Integer` | `__property int StartHour;` |
| `EndHour: Integer` | `Integer` | `__property int EndHour;` |
| `HTML: string (read-only)` | `string` | `__property UnicodeString HTML /* read-only */;` |
| `PageBuilder: TsgcHTMLPageBuilder` | [TsgcHTMLPageBuilder](../types/TsgcHTMLPageBuilder.md) | `__property TsgcHTMLPageBuilder * PageBuilder;` |
| `Section: string` | `string` | `__property UnicodeString Section;` |
| `SectionTitle: string` | `string` | `__property UnicodeString SectionTitle;` |
| `SectionOrder: Integer` | `Integer` | `__property int SectionOrder;` |
| `ColumnWidth: TsgcHTMLColWidth` | [TsgcHTMLColWidth](../types/TsgcHTMLColWidth.md) | `__property TsgcHTMLColWidth * ColumnWidth;` |
| `RowGroup: Integer` | `Integer` | `__property int RowGroup;` |
| `ComponentVisible: Boolean` | `Boolean` | `__property bool ComponentVisible;` |
| `DataSource: TDataSource` | `TDataSource` | `__property TDataSource * DataSource;` |
| `DataAutoRefresh: Boolean` | `Boolean` | `__property bool DataAutoRefresh;` |
| `HTMXEngine: TComponent` | `TComponent` | `__property TComponent * HTMXEngine;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnDataChanged: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDataChanged;` |
| `OnBeforeRefresh: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnBeforeRefresh;` |
| `OnAfterRefresh: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAfterRefresh;` |

## Methods

Delphi

```pascal
procedure AddEvent(const aTitle: string; aStart, aEnd: TDateTime; aColor: TsgcHTMLColor = hcPrimary; aAllDay: Boolean = False);
procedure LoadFromDataSet(aDataSet: TDataSet; const aTitleField, aStartField, aEndField: string);
```

C++Builder

```cpp
void __fastcall AddEvent(const UnicodeString aTitle, System::TDateTime aStart, System::TDateTime aEnd, TsgcHTMLColor * aColor = hcPrimary, bool aAllDay = False);
void __fastcall LoadFromDataSet(TDataSet * aDataSet, const UnicodeString aTitleField, const UnicodeString aStartField, const UnicodeString aEndField);
```

