# TsgcHTMLComponent_Popover

unit: sgcHTML_Component_Popover

Add `sgcHTML_Component_Popover` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Content: string` | `string` | `__property UnicodeString Content;` |
| `Title: string` | `string` | `__property UnicodeString Title;` |
| `Body: string` | `string` | `__property UnicodeString Body;` |
| `Placement: TsgcHTMLPlacement` | [TsgcHTMLPlacement](../types/TsgcHTMLPlacement.md) | `__property TsgcHTMLPlacement * Placement;` |
| `Trigger: TsgcHTMLPopoverTrigger` | [TsgcHTMLPopoverTrigger](../types/TsgcHTMLPopoverTrigger.md) | `__property TsgcHTMLPopoverTrigger * Trigger;` |
| `Dismissible: Boolean` | `Boolean` | `__property bool Dismissible;` |
| `PopoverID: string` | `string` | `__property UnicodeString PopoverID;` |
| `ContentStyle: TsgcHTMLButtonStyle` | [TsgcHTMLButtonStyle](../types/TsgcHTMLButtonStyle.md) | `__property TsgcHTMLButtonStyle * ContentStyle;` |
| `InitScript: string` | `string` | `__property UnicodeString InitScript;` |
| `AutoInit: Boolean` | `Boolean` | `__property bool AutoInit;` |
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

