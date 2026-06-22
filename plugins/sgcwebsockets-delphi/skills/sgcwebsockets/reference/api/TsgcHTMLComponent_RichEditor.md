# TsgcHTMLComponent_RichEditor

unit: sgcHTML_Component_RichEditor
Edition: All-Access

Add `sgcHTML_Component_RichEditor` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Content: string` | `string` | `__property UnicodeString Content;` |
| `Placeholder: string` | `string` | `__property UnicodeString Placeholder;` |
| `Height: string` | `string` | `__property UnicodeString Height;` |
| `Toolbar: TsgcHTMLRichEditorToolbar` | [TsgcHTMLRichEditorToolbar](../types/TsgcHTMLRichEditorToolbar.md) | `__property TsgcHTMLRichEditorToolbar * Toolbar;` |
| `Theme: TsgcHTMLRichEditorTheme` | [TsgcHTMLRichEditorTheme](../types/TsgcHTMLRichEditorTheme.md) | `__property TsgcHTMLRichEditorTheme * Theme;` |
| `ReadOnly: Boolean` | `Boolean` | `__property bool ReadOnly;` |
| `EditorID: string` | `string` | `__property UnicodeString EditorID;` |
| `Name: string` | `string` | `__property UnicodeString Name;` |
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

