# TsgcHTMLComponent_Image

unit: sgcHTML_Component_Image
Edition: All-Access

Add `sgcHTML_Component_Image` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Src: string` | `string` | `__property UnicodeString Src;` |
| `Alt: string` | `string` | `__property UnicodeString Alt;` |
| `Width: string` | `string` | `__property UnicodeString Width;` |
| `Height: string` | `string` | `__property UnicodeString Height;` |
| `Shape: TsgcHTMLImageShape` | [TsgcHTMLImageShape](../types/TsgcHTMLImageShape.md) | `__property TsgcHTMLImageShape * Shape;` |
| `Responsive: Boolean` | `Boolean` | `__property bool Responsive;` |
| `LazyLoad: Boolean` | `Boolean` | `__property bool LazyLoad;` |
| `Lightbox: Boolean` | `Boolean` | `__property bool Lightbox;` |
| `ImageID: string` | `string` | `__property UnicodeString ImageID;` |
| `Caption: string` | `string` | `__property UnicodeString Caption;` |
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

