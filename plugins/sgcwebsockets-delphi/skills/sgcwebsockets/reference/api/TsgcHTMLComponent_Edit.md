# TsgcHTMLComponent_Edit

unit: sgcHTML_Component_Edit
Edition: All-Access

Add `sgcHTML_Component_Edit` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Name: string` | `string` | `__property UnicodeString Name;` |
| `Label_: string` | `string` | `__property UnicodeString Label_;` |
| `Value: string` | `string` | `__property UnicodeString Value;` |
| `Placeholder: string` | `string` | `__property UnicodeString Placeholder;` |
| `InputType: TsgcHTMLInputType` | [TsgcHTMLInputType](../types/TsgcHTMLInputType.md) | `__property TsgcHTMLInputType * InputType;` |
| `Required: Boolean` | `Boolean` | `__property bool Required;` |
| `Disabled: Boolean` | `Boolean` | `__property bool Disabled;` |
| `ReadOnly: Boolean` | `Boolean` | `__property bool ReadOnly;` |
| `EditID: string` | `string` | `__property UnicodeString EditID;` |
| `HelpText: string` | `string` | `__property UnicodeString HelpText;` |
| `DataField: string` | `string` | `__property UnicodeString DataField;` |
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

