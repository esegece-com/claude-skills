# TsgcHTMLComponent_ListGroup

unit: sgcHTML_Component_ListGroup
Edition: All-Access

Add `sgcHTML_Component_ListGroup` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Items: TsgcHTMLListGroupItems` | [TsgcHTMLListGroupItems](../types/TsgcHTMLListGroupItems.md) | `__property TsgcHTMLListGroupItems * Items;` |
| `Flush: Boolean` | `Boolean` | `__property bool Flush;` |
| `Numbered: Boolean` | `Boolean` | `__property bool Numbered;` |
| `Horizontal: Boolean` | `Boolean` | `__property bool Horizontal;` |
| `ListGroupID: string` | `string` | `__property UnicodeString ListGroupID;` |
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
procedure AddItem(const aText: string; const aHref: string = ''; const aBadge: string = ''; aBadgeStyle: TsgcHTMLBadgeStyle = bgPrimary);
procedure LoadFromDataSet(aDataSet: TDataSet; const aTextField: string; const aHrefField: string = ''; const aBadgeField: string = '');
```

C++Builder

```cpp
void __fastcall AddItem(const UnicodeString aText, const UnicodeString aHref = '', const UnicodeString aBadge = '', TsgcHTMLBadgeStyle * aBadgeStyle = bgPrimary);
void __fastcall LoadFromDataSet(TDataSet * aDataSet, const UnicodeString aTextField, const UnicodeString aHrefField = '', const UnicodeString aBadgeField = '');
```

