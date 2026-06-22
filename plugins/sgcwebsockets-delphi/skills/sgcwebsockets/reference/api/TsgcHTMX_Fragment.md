# TsgcHTMX_Fragment

unit: sgcHTMX_Fragment
Edition: requires SGC_HTMX

Add `sgcHTMX_Fragment` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `TargetID: string` | `string` | `__property UnicodeString TargetID;` |
| `SwapMode: TsgcHTMXSwapMode` | [TsgcHTMXSwapMode](../types/TsgcHTMXSwapMode.md) | `__property TsgcHTMXSwapMode * SwapMode;` |
| `SwapOOB: Boolean` | `Boolean` | `__property bool SwapOOB;` |
| `Content: string` | `string` | `__property UnicodeString Content;` |
| `Tag: string` | `string` | `__property UnicodeString Tag;` |
| `CSSID: string` | `string` | `__property UnicodeString CSSID;` |
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
function GetOOBFragment: string;
```

C++Builder

```cpp
UnicodeString __fastcall GetOOBFragment();
```

