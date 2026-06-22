# TsgcHTMLComponent_Dropdown

unit: sgcHTML_Component_Dropdown

Add `sgcHTML_Component_Dropdown` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Items: TsgcHTMLDropdownItems` | [TsgcHTMLDropdownItems](../types/TsgcHTMLDropdownItems.md) | `__property TsgcHTMLDropdownItems * Items;` |
| `ButtonText: string` | `string` | `__property UnicodeString ButtonText;` |
| `ButtonClass: string` | `string` | `__property UnicodeString ButtonClass;` |
| `DropdownID: string` | `string` | `__property UnicodeString DropdownID;` |
| `Split: Boolean` | `Boolean` | `__property bool Split;` |
| `ButtonStyleEnum: TsgcHTMLButtonStyle` | [TsgcHTMLButtonStyle](../types/TsgcHTMLButtonStyle.md) | `__property TsgcHTMLButtonStyle * ButtonStyleEnum;` |
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

