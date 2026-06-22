# TsgcHTMLComponent_Gauge

unit: sgcHTML_Component_Gauge

Add `sgcHTML_Component_Gauge` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Value: Double` | `Double` | `__property double Value;` |
| `MinValue: Double` | `Double` | `__property double MinValue;` |
| `MaxValue: Double` | `Double` | `__property double MaxValue;` |
| `Title: string` | `string` | `__property UnicodeString Title;` |
| `Unit_: string` | `string` | `__property UnicodeString Unit_;` |
| `GaugeID: string` | `string` | `__property UnicodeString GaugeID;` |
| `Width: Integer` | `Integer` | `__property int Width;` |
| `ColorLow: string` | `string` | `__property UnicodeString ColorLow;` |
| `ColorMid: string` | `string` | `__property UnicodeString ColorMid;` |
| `ColorHigh: string` | `string` | `__property UnicodeString ColorHigh;` |
| `ThresholdMid: Double` | `Double` | `__property double ThresholdMid;` |
| `ThresholdHigh: Double` | `Double` | `__property double ThresholdHigh;` |
| `ColorLowStyle: TsgcHTMLColor` | [TsgcHTMLColor](../types/TsgcHTMLColor.md) | `__property TsgcHTMLColor * ColorLowStyle;` |
| `ColorMidStyle: TsgcHTMLColor` | [TsgcHTMLColor](../types/TsgcHTMLColor.md) | `__property TsgcHTMLColor * ColorMidStyle;` |
| `ColorHighStyle: TsgcHTMLColor` | [TsgcHTMLColor](../types/TsgcHTMLColor.md) | `__property TsgcHTMLColor * ColorHighStyle;` |
| `BackgroundArcColor: string` | `string` | `__property UnicodeString BackgroundArcColor;` |
| `BackgroundArcColorStyle: TsgcHTMLColor` | [TsgcHTMLColor](../types/TsgcHTMLColor.md) | `__property TsgcHTMLColor * BackgroundArcColorStyle;` |
| `ArcStrokeWidth: Integer` | `Integer` | `__property int ArcStrokeWidth;` |
| `ValueFontSize: Integer` | `Integer` | `__property int ValueFontSize;` |
| `UnitFontSize: Integer` | `Integer` | `__property int UnitFontSize;` |
| `LabelFontSize: Integer` | `Integer` | `__property int LabelFontSize;` |
| `LabelColor: string` | `string` | `__property UnicodeString LabelColor;` |
| `LabelColorStyle: TsgcHTMLColor` | [TsgcHTMLColor](../types/TsgcHTMLColor.md) | `__property TsgcHTMLColor * LabelColorStyle;` |
| `SvgViewBox: string` | `string` | `__property UnicodeString SvgViewBox;` |
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

