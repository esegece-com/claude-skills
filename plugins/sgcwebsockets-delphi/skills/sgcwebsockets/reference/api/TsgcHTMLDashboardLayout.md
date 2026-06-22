# TsgcHTMLDashboardLayout

unit: sgcHTML_Component_DashboardLayout
Edition: All-Access

Add `sgcHTML_Component_DashboardLayout` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Sidebar: TsgcHTMLComponent_Sidebar (read-only)` | [TsgcHTMLComponent_Sidebar](../types/TsgcHTMLComponent_Sidebar.md) | `__property TsgcHTMLComponent_Sidebar * Sidebar /* read-only */;` |
| `FooterText: string` | `string` | `__property UnicodeString FooterText;` |
| `Fluid: Boolean` | `Boolean` | `__property bool Fluid;` |
| `DarkMode: Boolean` | `Boolean` | `__property bool DarkMode;` |
| `LayoutID: string` | `string` | `__property UnicodeString LayoutID;` |
| `MainPadding: string` | `string` | `__property UnicodeString MainPadding;` |
| `MainMinHeight: string` | `string` | `__property UnicodeString MainMinHeight;` |
| `SectionMarginBottom: string` | `string` | `__property UnicodeString SectionMarginBottom;` |
| `SectionTitleBorderColor: string` | `string` | `__property UnicodeString SectionTitleBorderColor;` |
| `SectionTitleBorderColorStyle: TsgcHTMLColor` | [TsgcHTMLColor](../types/TsgcHTMLColor.md) | `__property TsgcHTMLColor * SectionTitleBorderColorStyle;` |
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
procedure AddSection(const aTitle, aContent: string; const aID: string = '');
procedure AddRawContent(const aContent: string);
procedure ClearContent;
```

C++Builder

```cpp
void __fastcall AddSection(const UnicodeString aTitle, const UnicodeString aContent, const UnicodeString aID = '');
void __fastcall AddRawContent(const UnicodeString aContent);
void __fastcall ClearContent();
```

