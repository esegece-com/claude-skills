# TsgcHTMLComponent_Modal

unit: sgcHTML_Component_Modal
Edition: All-Access

Add `sgcHTML_Component_Modal` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Title: string` | `string` | `__property UnicodeString Title;` |
| `Body: string` | `string` | `__property UnicodeString Body;` |
| `Footer: string` | `string` | `__property UnicodeString Footer;` |
| `ModalID: string` | `string` | `__property UnicodeString ModalID;` |
| `Size: TsgcHTMLModalSize` | [TsgcHTMLModalSize](../types/TsgcHTMLModalSize.md) | `__property TsgcHTMLModalSize * Size;` |
| `Centered: Boolean` | `Boolean` | `__property bool Centered;` |
| `Scrollable: Boolean` | `Boolean` | `__property bool Scrollable;` |
| `StaticBackdrop: Boolean` | `Boolean` | `__property bool StaticBackdrop;` |
| `ShowClose: Boolean` | `Boolean` | `__property bool ShowClose;` |
| `CSSClass: string` | `string` | `__property UnicodeString CSSClass;` |
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
procedure AddFooterButton(const aText: string; aStyle: TsgcHTMLButtonStyle; aCloseOnClick: Boolean = False);
```

C++Builder

```cpp
void __fastcall AddFooterButton(const UnicodeString aText, TsgcHTMLButtonStyle * aStyle, bool aCloseOnClick = False);
```

