# TsgcHTMLComponent_KanbanBoard

unit: sgcHTML_Component_KanbanBoard
Edition: All-Access

Add `sgcHTML_Component_KanbanBoard` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Columns: TsgcHTMLKanbanColumns` | [TsgcHTMLKanbanColumns](../types/TsgcHTMLKanbanColumns.md) | `__property TsgcHTMLKanbanColumns * Columns;` |
| `BoardID: string` | `string` | `__property UnicodeString BoardID;` |
| `Height: string` | `string` | `__property UnicodeString Height;` |
| `DragEnabled: Boolean` | `Boolean` | `__property bool DragEnabled;` |
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
function AddColumn(const aTitle: string; aColor: TsgcHTMLColor = hcPrimary) : TsgcHTMLKanbanColumn;
procedure LoadFromDataSet(aDataSet: TDataSet; const aGroupField, aTitleField: string; const aDescField: string = ''; const aAssigneeField: string = '');
```

C++Builder

```cpp
TsgcHTMLKanbanColumn * __fastcall AddColumn(const UnicodeString aTitle, TsgcHTMLColor * aColor = hcPrimary);
void __fastcall LoadFromDataSet(TDataSet * aDataSet, const UnicodeString aGroupField, const UnicodeString aTitleField, const UnicodeString aDescField = '', const UnicodeString aAssigneeField = '');
```

