# TsgcHTMLComponent_Chart

unit: sgcHTML_Component_Chart
Edition: All-Access

Add `sgcHTML_Component_Chart` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `ChartType: TsgcHTMLChartType` | [TsgcHTMLChartType](../types/TsgcHTMLChartType.md) | `__property TsgcHTMLChartType * ChartType;` |
| `Labels: string` | `string` | `__property UnicodeString Labels;` |
| `Datasets: TsgcHTMLChartDatasets` | [TsgcHTMLChartDatasets](../types/TsgcHTMLChartDatasets.md) | `__property TsgcHTMLChartDatasets * Datasets;` |
| `ChartID: string` | `string` | `__property UnicodeString ChartID;` |
| `Width: string` | `string` | `__property UnicodeString Width;` |
| `Height: string` | `string` | `__property UnicodeString Height;` |
| `Title: string` | `string` | `__property UnicodeString Title;` |
| `ShowLegend: Boolean` | `Boolean` | `__property bool ShowLegend;` |
| `Responsive: Boolean` | `Boolean` | `__property bool Responsive;` |
| `CustomOptions: string` | `string` | `__property UnicodeString CustomOptions;` |
| `Stacked: Boolean` | `Boolean` | `__property bool Stacked;` |
| `PointRadius: Integer` | `Integer` | `__property int PointRadius;` |
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
procedure AddLabel(const aLabel: string);
procedure AddDataset(const aLabel: string; const aData: array of Double; const aBorderColor: string = ''; const aBackgroundColor: string = ''; aFill: Boolean = False);
procedure ClearData;
procedure LoadFromDataSet(aDataSet: TDataSet; const aLabelField: string; const aValueFields: array of string);
```

C++Builder

```cpp
void __fastcall AddLabel(const UnicodeString aLabel);
void __fastcall AddDataset(const UnicodeString aLabel, const array of Double aData, const UnicodeString aBorderColor = '', const UnicodeString aBackgroundColor = '', bool aFill = False);
void __fastcall ClearData();
void __fastcall LoadFromDataSet(TDataSet * aDataSet, const UnicodeString aLabelField, const array of string aValueFields);
```

