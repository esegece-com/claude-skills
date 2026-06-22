# TsgcHTMLComponent_DataTable

unit: sgcHTML_Component_DataTable

Add `sgcHTML_Component_DataTable` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Grid: TsgcHTMLComponent_Grid (read-only)` | [TsgcHTMLComponent_Grid](../types/TsgcHTMLComponent_Grid.md) | `__property TsgcHTMLComponent_Grid * Grid /* read-only */;` |
| `Pagination: TsgcHTMLComponent_Pagination (read-only)` | [TsgcHTMLComponent_Pagination](../types/TsgcHTMLComponent_Pagination.md) | `__property TsgcHTMLComponent_Pagination * Pagination /* read-only */;` |
| `ShowSearch: Boolean` | `Boolean` | `__property bool ShowSearch;` |
| `SearchPlaceholder: string` | `string` | `__property UnicodeString SearchPlaceholder;` |
| `ShowRowCount: Boolean` | `Boolean` | `__property bool ShowRowCount;` |
| `ShowExport: Boolean` | `Boolean` | `__property bool ShowExport;` |
| `ShowPageSize: Boolean` | `Boolean` | `__property bool ShowPageSize;` |
| `PageSizes: string` | `string` | `__property UnicodeString PageSizes;` |
| `Title: string` | `string` | `__property UnicodeString Title;` |
| `TableID: string` | `string` | `__property UnicodeString TableID;` |
| `SearchAction: string` | `string` | `__property UnicodeString SearchAction;` |
| `ToolbarClass: string` | `string` | `__property UnicodeString ToolbarClass;` |
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
procedure LoadFromDataSet(aDataSet: TDataSet; aPageSize: Integer = 10);
```

C++Builder

```cpp
void __fastcall LoadFromDataSet(TDataSet * aDataSet, int aPageSize = 10);
```

