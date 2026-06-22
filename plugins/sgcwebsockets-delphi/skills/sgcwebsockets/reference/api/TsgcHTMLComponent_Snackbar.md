# TsgcHTMLComponent_Snackbar

unit: sgcHTML_Component_Snackbar
Edition: All-Access

Add `sgcHTML_Component_Snackbar` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Message: string` | `string` | `__property UnicodeString Message;` |
| `ActionText: string` | `string` | `__property UnicodeString ActionText;` |
| `ActionHref: string` | `string` | `__property UnicodeString ActionHref;` |
| `Color: TsgcHTMLColor` | [TsgcHTMLColor](../types/TsgcHTMLColor.md) | `__property TsgcHTMLColor * Color;` |
| `Position: TsgcHTMLSnackbarPosition` | [TsgcHTMLSnackbarPosition](../types/TsgcHTMLSnackbarPosition.md) | `__property TsgcHTMLSnackbarPosition * Position;` |
| `AutoHide: Boolean` | `Boolean` | `__property bool AutoHide;` |
| `Delay: Integer` | `Integer` | `__property int Delay;` |
| `SnackbarID: string` | `string` | `__property UnicodeString SnackbarID;` |
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

