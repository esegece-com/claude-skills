# TsgcHTMLComponent_Toolbar

unit: sgcHTML_Component_Toolbar
Edition: All-Access

Add `sgcHTML_Component_Toolbar` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Items: TsgcHTMLToolbarItems` | [TsgcHTMLToolbarItems](../types/TsgcHTMLToolbarItems.md) | `__property TsgcHTMLToolbarItems * Items;` |
| `Size: TsgcHTMLToolbarSize` | [TsgcHTMLToolbarSize](../types/TsgcHTMLToolbarSize.md) | `__property TsgcHTMLToolbarSize * Size;` |
| `ToolbarID: string` | `string` | `__property UnicodeString ToolbarID;` |
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
procedure AddButton(const aText: string; aStyle: TsgcHTMLButtonStyle = bsOutlinePrimary; const aHref: string = '');
procedure AddSeparator;
```

C++Builder

```cpp
void __fastcall AddButton(const UnicodeString aText, TsgcHTMLButtonStyle * aStyle = bsOutlinePrimary, const UnicodeString aHref = '');
void __fastcall AddSeparator();
```

