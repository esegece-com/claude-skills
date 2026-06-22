# TsgcHTMLComponent_Grid

kind: class
unit: sgcHTML_Component_Grid

## Properties

| Delphi | Type |
| --- | --- |
| `Columns: TsgcHTMLGridColumns` | [TsgcHTMLGridColumns](./TsgcHTMLGridColumns.md) |
| `Rows: TStringList` | `TStringList` |
| `Striped: Boolean` | `Boolean` |
| `Bordered: Boolean` | `Boolean` |
| `Hover: Boolean` | `Boolean` |
| `Responsive: Boolean` | `Boolean` |
| `Dark: Boolean` | `Boolean` |
| `TableID: string` | `string` |
| `CSSClass: string` | `string` |
| `ShowSort: Boolean` | `Boolean` |
| `ShowFilter: Boolean` | `Boolean` |
| `ShowExport: Boolean` | `Boolean` |
| `ExportFileName: string` | `string` |
| `InlineEdit: Boolean` | `Boolean` |
| `EditMode: TsgcHTMLGridEditMode` | [TsgcHTMLGridEditMode](./TsgcHTMLGridEditMode.md) |
| `GroupByColumn: string` | `string` |
| `ShowGrouping: Boolean` | `Boolean` |
| `ColumnReorder: Boolean` | `Boolean` |
| `VirtualScroll: Boolean` | `Boolean` |
| `VirtualScrollURL: string` | `string` |
| `VisibleRows: Integer` | `Integer` |
| `AIQueryEnabled: Boolean` | `Boolean` |
| `AIQueryPlaceholder: string` | `string` |
| `AIQueryButtonText: string` | `string` |
| `AIQueryButtonStyle: TsgcHTMLButtonStyle` | [TsgcHTMLButtonStyle](./TsgcHTMLButtonStyle.md) |
| `HTML: string (read-only)` | `string` |
| `PageBuilder: TsgcHTMLPageBuilder` | [TsgcHTMLPageBuilder](./TsgcHTMLPageBuilder.md) |
| `Section: string` | `string` |
| `SectionTitle: string` | `string` |
| `SectionOrder: Integer` | `Integer` |
| `ColumnWidth: TsgcHTMLColWidth` | [TsgcHTMLColWidth](./TsgcHTMLColWidth.md) |
| `RowGroup: Integer` | `Integer` |
| `ComponentVisible: Boolean` | `Boolean` |
| `DataSource: TDataSource` | `TDataSource` |
| `DataAutoRefresh: Boolean` | `Boolean` |
| `HTMXEngine: TComponent` | `TComponent` |
| `Version: String (read-only)` | `String` |

## Events

| Delphi | Type |
| --- | --- |
| `OnAIQuery: TsgcGridAIQueryEvent` | [TsgcGridAIQueryEvent](./TsgcGridAIQueryEvent.md) |
| `OnDataChanged: TNotifyEvent` | `TNotifyEvent` |
| `OnBeforeRefresh: TNotifyEvent` | `TNotifyEvent` |
| `OnAfterRefresh: TNotifyEvent` | `TNotifyEvent` |

## Methods

```pascal
procedure Clear;
procedure AddRow(const aValues: array of string);
procedure LoadFromDataSet(aDataSet: TDataSet);
procedure ProcessAIQuery(const aQuery: string);
```

