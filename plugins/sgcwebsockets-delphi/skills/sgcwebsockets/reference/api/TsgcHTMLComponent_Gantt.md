# TsgcHTMLComponent_Gantt

unit: sgcHTML_Component_Gantt
Edition: All-Access

Add `sgcHTML_Component_Gantt` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Tasks: TsgcHTMLGanttTasks` | [TsgcHTMLGanttTasks](../types/TsgcHTMLGanttTasks.md) | `__property TsgcHTMLGanttTasks * Tasks;` |
| `GanttID: string` | `string` | `__property UnicodeString GanttID;` |
| `Title: string` | `string` | `__property UnicodeString Title;` |
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
procedure AddTask(const aTitle: string; aStart, aEnd: TDateTime; aProgress: Integer = 0; aColor: TsgcHTMLColor = hcPrimary; const aAssignee: string = '');
```

C++Builder

```cpp
void __fastcall AddTask(const UnicodeString aTitle, System::TDateTime aStart, System::TDateTime aEnd, int aProgress = 0, TsgcHTMLColor * aColor = hcPrimary, const UnicodeString aAssignee = '');
```

