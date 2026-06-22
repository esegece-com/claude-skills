# TsgcHTMLComponent_Pagination

unit: sgcHTML_Component_Pagination
Edition: All-Access

Add `sgcHTML_Component_Pagination` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `CurrentPage: Integer` | `Integer` | `__property int CurrentPage;` |
| `TotalPages: Integer` | `Integer` | `__property int TotalPages;` |
| `BaseURL: string` | `string` | `__property UnicodeString BaseURL;` |
| `Size: TsgcHTMLPaginationSize` | [TsgcHTMLPaginationSize](../types/TsgcHTMLPaginationSize.md) | `__property TsgcHTMLPaginationSize * Size;` |
| `Align: TsgcHTMLPaginationAlign` | [TsgcHTMLPaginationAlign](../types/TsgcHTMLPaginationAlign.md) | `__property TsgcHTMLPaginationAlign * Align;` |
| `ShowPrevNext: Boolean` | `Boolean` | `__property bool ShowPrevNext;` |
| `ShowFirstLast: Boolean` | `Boolean` | `__property bool ShowFirstLast;` |
| `MaxVisible: Integer` | `Integer` | `__property int MaxVisible;` |
| `PaginationID: string` | `string` | `__property UnicodeString PaginationID;` |
| `TotalItems: Integer` | `Integer` | `__property int TotalItems;` |
| `PageSize: Integer` | `Integer` | `__property int PageSize;` |
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

