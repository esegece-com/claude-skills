# TsgcHTMLComponent_Form

unit: sgcHTML_Component_Form
Edition: All-Access

Add `sgcHTML_Component_Form` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Fields: TsgcHTMLFormFields` | [TsgcHTMLFormFields](../types/TsgcHTMLFormFields.md) | `__property TsgcHTMLFormFields * Fields;` |
| `Action: string` | `string` | `__property UnicodeString Action;` |
| `Method: TsgcHTMLFormMethod` | [TsgcHTMLFormMethod](../types/TsgcHTMLFormMethod.md) | `__property TsgcHTMLFormMethod * Method;` |
| `FormID: string` | `string` | `__property UnicodeString FormID;` |
| `Layout: TsgcHTMLFormLayout` | [TsgcHTMLFormLayout](../types/TsgcHTMLFormLayout.md) | `__property TsgcHTMLFormLayout * Layout;` |
| `LabelColWidth: Integer` | `Integer` | `__property int LabelColWidth;` |
| `FieldColWidth: Integer` | `Integer` | `__property int FieldColWidth;` |
| `CSSClass: string` | `string` | `__property UnicodeString CSSClass;` |
| `SubmitText: string` | `string` | `__property UnicodeString SubmitText;` |
| `SubmitClass: string` | `string` | `__property UnicodeString SubmitClass;` |
| `ShowReset: Boolean` | `Boolean` | `__property bool ShowReset;` |
| `ResetText: string` | `string` | `__property UnicodeString ResetText;` |
| `SubmitStyle: TsgcHTMLButtonStyle` | [TsgcHTMLButtonStyle](../types/TsgcHTMLButtonStyle.md) | `__property TsgcHTMLButtonStyle * SubmitStyle;` |
| `AIBuildEnabled: Boolean` | `Boolean` | `__property bool AIBuildEnabled;` |
| `AIBuildPlaceholder: string` | `string` | `__property UnicodeString AIBuildPlaceholder;` |
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
| `OnAIBuildForm: TsgcFormAIBuildEvent` | [TsgcFormAIBuildEvent](../types/TsgcFormAIBuildEvent.md) | `__property TsgcFormAIBuildEvent OnAIBuildForm;` |
| `OnDataChanged: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDataChanged;` |
| `OnBeforeRefresh: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnBeforeRefresh;` |
| `OnAfterRefresh: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAfterRefresh;` |

## Methods

Delphi

```pascal
procedure LoadFromDataSet(aDataSet: TDataSet);
procedure LoadValuesFromDataSet(aDataSet: TDataSet);
procedure BuildFromAIDescription(const aDescription: string);
procedure LoadFieldsFromJSON(const aJSON: string);
```

C++Builder

```cpp
void __fastcall LoadFromDataSet(TDataSet * aDataSet);
void __fastcall LoadValuesFromDataSet(TDataSet * aDataSet);
void __fastcall BuildFromAIDescription(const UnicodeString aDescription);
void __fastcall LoadFieldsFromJSON(const UnicodeString aJSON);
```

