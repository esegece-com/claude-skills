# TsgcHTMLComponent_NavBar

unit: sgcHTML_Component_NavBar

Add `sgcHTML_Component_NavBar` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Brand: string` | `string` | `__property UnicodeString Brand;` |
| `BrandHref: string` | `string` | `__property UnicodeString BrandHref;` |
| `Items: TsgcHTMLNavItems` | [TsgcHTMLNavItems](../types/TsgcHTMLNavItems.md) | `__property TsgcHTMLNavItems * Items;` |
| `Theme: TsgcHTMLNavBarTheme` | [TsgcHTMLNavBarTheme](../types/TsgcHTMLNavBarTheme.md) | `__property TsgcHTMLNavBarTheme * Theme;` |
| `Expand: TsgcHTMLNavBarExpand` | [TsgcHTMLNavBarExpand](../types/TsgcHTMLNavBarExpand.md) | `__property TsgcHTMLNavBarExpand * Expand;` |
| `Fluid: Boolean` | `Boolean` | `__property bool Fluid;` |
| `NavBarID: string` | `string` | `__property UnicodeString NavBarID;` |
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

