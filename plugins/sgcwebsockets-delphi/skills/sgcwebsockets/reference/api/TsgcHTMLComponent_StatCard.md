# TsgcHTMLComponent_StatCard

unit: sgcHTML_Component_StatCard
Edition: All-Access

Add `sgcHTML_Component_StatCard` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Title: string` | `string` | `__property UnicodeString Title;` |
| `Value: string` | `string` | `__property UnicodeString Value;` |
| `Icon: string` | `string` | `__property UnicodeString Icon;` |
| `Trend: TsgcHTMLStatTrend` | [TsgcHTMLStatTrend](../types/TsgcHTMLStatTrend.md) | `__property TsgcHTMLStatTrend * Trend;` |
| `TrendValue: string` | `string` | `__property UnicodeString TrendValue;` |
| `Color: TsgcHTMLStatColor` | [TsgcHTMLStatColor](../types/TsgcHTMLStatColor.md) | `__property TsgcHTMLStatColor * Color;` |
| `CardID: string` | `string` | `__property UnicodeString CardID;` |
| `CSSClass: string` | `string` | `__property UnicodeString CSSClass;` |
| `FooterText: string` | `string` | `__property UnicodeString FooterText;` |
| `Gradient: TsgcHTMLStatGradient` | [TsgcHTMLStatGradient](../types/TsgcHTMLStatGradient.md) | `__property TsgcHTMLStatGradient * Gradient;` |
| `GradientStartColor: string` | `string` | `__property UnicodeString GradientStartColor;` |
| `GradientEndColor: string` | `string` | `__property UnicodeString GradientEndColor;` |
| `GradientAngle: Integer` | `Integer` | `__property int GradientAngle;` |
| `GradientBorderRadius: string` | `string` | `__property UnicodeString GradientBorderRadius;` |
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
function GetInnerHTML: string;
```

C++Builder

```cpp
UnicodeString __fastcall GetInnerHTML();
```

