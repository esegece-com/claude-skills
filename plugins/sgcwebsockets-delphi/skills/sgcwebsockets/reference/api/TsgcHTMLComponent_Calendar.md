# TsgcHTMLComponent_Calendar

unit: sgcHTML_Component_Calendar

Add `sgcHTML_Component_Calendar` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Year: Integer` | `Integer` | `__property int Year;` |
| `Month: Integer` | `Integer` | `__property int Month;` |
| `Events: TsgcHTMLCalendarEvents` | [TsgcHTMLCalendarEvents](../types/TsgcHTMLCalendarEvents.md) | `__property TsgcHTMLCalendarEvents * Events;` |
| `CalendarID: string` | `string` | `__property UnicodeString CalendarID;` |
| `HighlightToday: Boolean` | `Boolean` | `__property bool HighlightToday;` |
| `ShowNavigation: Boolean` | `Boolean` | `__property bool ShowNavigation;` |
| `PrevURL: string` | `string` | `__property UnicodeString PrevURL;` |
| `NextURL: string` | `string` | `__property UnicodeString NextURL;` |
| `TodayClass: string` | `string` | `__property UnicodeString TodayClass;` |
| `NavButtonClass: string` | `string` | `__property UnicodeString NavButtonClass;` |
| `TableClass: string` | `string` | `__property UnicodeString TableClass;` |
| `EventDotSize: Integer` | `Integer` | `__property int EventDotSize;` |
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
procedure LoadFromDataSet(aDataSet: TDataSet; const aDateField, aTitleField: string);
```

C++Builder

```cpp
void __fastcall LoadFromDataSet(TDataSet * aDataSet, const UnicodeString aDateField, const UnicodeString aTitleField);
```

