# TsgcHTMLComponent_Timeline

unit: sgcHTML_Component_Timeline
Edition: All-Access

Add `sgcHTML_Component_Timeline` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Items: TsgcHTMLTimelineItems` | [TsgcHTMLTimelineItems](../types/TsgcHTMLTimelineItems.md) | `__property TsgcHTMLTimelineItems * Items;` |
| `TimelineID: string` | `string` | `__property UnicodeString TimelineID;` |
| `LineColor: string` | `string` | `__property UnicodeString LineColor;` |
| `LineColorStyle: TsgcHTMLColor` | [TsgcHTMLColor](../types/TsgcHTMLColor.md) | `__property TsgcHTMLColor * LineColorStyle;` |
| `LineWidth: Integer` | `Integer` | `__property int LineWidth;` |
| `DotSize: Integer` | `Integer` | `__property int DotSize;` |
| `TimeColor: string` | `string` | `__property UnicodeString TimeColor;` |
| `TimeColorStyle: TsgcHTMLColor` | [TsgcHTMLColor](../types/TsgcHTMLColor.md) | `__property TsgcHTMLColor * TimeColorStyle;` |
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
procedure LoadFromDataSet(aDataSet: TDataSet; const aTitleField: string; const aContentField: string = ''; const aTimestampField: string = '');
```

C++Builder

```cpp
void __fastcall LoadFromDataSet(TDataSet * aDataSet, const UnicodeString aTitleField, const UnicodeString aContentField = '', const UnicodeString aTimestampField = '');
```

