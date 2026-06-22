# TsgcHTMLComponent_Grid

unit: sgcHTML_Component_Grid

Add `sgcHTML_Component_Grid` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Columns: TsgcHTMLGridColumns` | [TsgcHTMLGridColumns](../types/TsgcHTMLGridColumns.md) | `__property TsgcHTMLGridColumns * Columns;` |
| `Rows: TStringList` | `TStringList` | `__property TStringList * Rows;` |
| `Striped: Boolean` | `Boolean` | `__property bool Striped;` |
| `Bordered: Boolean` | `Boolean` | `__property bool Bordered;` |
| `Hover: Boolean` | `Boolean` | `__property bool Hover;` |
| `Responsive: Boolean` | `Boolean` | `__property bool Responsive;` |
| `Dark: Boolean` | `Boolean` | `__property bool Dark;` |
| `TableID: string` | `string` | `__property UnicodeString TableID;` |
| `CSSClass: string` | `string` | `__property UnicodeString CSSClass;` |
| `ShowSort: Boolean` | `Boolean` | `__property bool ShowSort;` |
| `ShowFilter: Boolean` | `Boolean` | `__property bool ShowFilter;` |
| `ShowExport: Boolean` | `Boolean` | `__property bool ShowExport;` |
| `ExportFileName: string` | `string` | `__property UnicodeString ExportFileName;` |
| `InlineEdit: Boolean` | `Boolean` | `__property bool InlineEdit;` |
| `EditMode: TsgcHTMLGridEditMode` | [TsgcHTMLGridEditMode](../types/TsgcHTMLGridEditMode.md) | `__property TsgcHTMLGridEditMode * EditMode;` |
| `GroupByColumn: string` | `string` | `__property UnicodeString GroupByColumn;` |
| `ShowGrouping: Boolean` | `Boolean` | `__property bool ShowGrouping;` |
| `ColumnReorder: Boolean` | `Boolean` | `__property bool ColumnReorder;` |
| `VirtualScroll: Boolean` | `Boolean` | `__property bool VirtualScroll;` |
| `VirtualScrollURL: string` | `string` | `__property UnicodeString VirtualScrollURL;` |
| `VisibleRows: Integer` | `Integer` | `__property int VisibleRows;` |
| `AIQueryEnabled: Boolean` | `Boolean` | `__property bool AIQueryEnabled;` |
| `AIQueryPlaceholder: string` | `string` | `__property UnicodeString AIQueryPlaceholder;` |
| `AIQueryButtonText: string` | `string` | `__property UnicodeString AIQueryButtonText;` |
| `AIQueryButtonStyle: TsgcHTMLButtonStyle` | [TsgcHTMLButtonStyle](../types/TsgcHTMLButtonStyle.md) | `__property TsgcHTMLButtonStyle * AIQueryButtonStyle;` |
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
| `OnAIQuery: TsgcGridAIQueryEvent` | [TsgcGridAIQueryEvent](../types/TsgcGridAIQueryEvent.md) | `__property TsgcGridAIQueryEvent OnAIQuery;` |
| `OnDataChanged: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDataChanged;` |
| `OnBeforeRefresh: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnBeforeRefresh;` |
| `OnAfterRefresh: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAfterRefresh;` |

## Methods

Delphi

```pascal
procedure Clear;
procedure AddRow(const aValues: array of string);
procedure LoadFromDataSet(aDataSet: TDataSet);
procedure ProcessAIQuery(const aQuery: string);
```

C++Builder

```cpp
void __fastcall Clear();
void __fastcall AddRow(const array of string aValues);
void __fastcall LoadFromDataSet(TDataSet * aDataSet);
void __fastcall ProcessAIQuery(const UnicodeString aQuery);
```

