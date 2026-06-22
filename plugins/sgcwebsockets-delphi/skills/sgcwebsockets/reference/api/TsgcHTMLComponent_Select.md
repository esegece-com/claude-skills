# TsgcHTMLComponent_Select

unit: sgcHTML_Component_Select
Edition: All-Access

Add `sgcHTML_Component_Select` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Options: TsgcHTMLSelectOptions` | [TsgcHTMLSelectOptions](../types/TsgcHTMLSelectOptions.md) | `__property TsgcHTMLSelectOptions * Options;` |
| `Name: string` | `string` | `__property UnicodeString Name;` |
| `Label_: string` | `string` | `__property UnicodeString Label_;` |
| `Placeholder: string` | `string` | `__property UnicodeString Placeholder;` |
| `Multiple: Boolean` | `Boolean` | `__property bool Multiple;` |
| `Size: TsgcHTMLSelectSize` | [TsgcHTMLSelectSize](../types/TsgcHTMLSelectSize.md) | `__property TsgcHTMLSelectSize * Size;` |
| `SelectID: string` | `string` | `__property UnicodeString SelectID;` |
| `Required: Boolean` | `Boolean` | `__property bool Required;` |
| `Disabled: Boolean` | `Boolean` | `__property bool Disabled;` |
| `VisibleItems: Integer` | `Integer` | `__property int VisibleItems;` |
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
procedure AddOption(const aValue, aText: string; aSelected: Boolean = False);
procedure AddOptionGroup(const aGroup, aValue, aText: string);
procedure LoadFromDataSet(aDataSet: TDataSet; const aValueField, aTextField: string; const aGroupField: string = '');
```

C++Builder

```cpp
void __fastcall AddOption(const UnicodeString aValue, const UnicodeString aText, bool aSelected = False);
void __fastcall AddOptionGroup(const UnicodeString aGroup, const UnicodeString aValue, const UnicodeString aText);
void __fastcall LoadFromDataSet(TDataSet * aDataSet, const UnicodeString aValueField, const UnicodeString aTextField, const UnicodeString aGroupField = '');
```

