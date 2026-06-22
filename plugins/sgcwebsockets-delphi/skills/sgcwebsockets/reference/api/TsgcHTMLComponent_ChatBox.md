# TsgcHTMLComponent_ChatBox

unit: sgcHTML_Component_ChatBox

Add `sgcHTML_Component_ChatBox` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Messages: TsgcHTMLChatMessages` | [TsgcHTMLChatMessages](../types/TsgcHTMLChatMessages.md) | `__property TsgcHTMLChatMessages * Messages;` |
| `ChatID: string` | `string` | `__property UnicodeString ChatID;` |
| `Height: string` | `string` | `__property UnicodeString Height;` |
| `ShowInput: Boolean` | `Boolean` | `__property bool ShowInput;` |
| `InputPlaceholder: string` | `string` | `__property UnicodeString InputPlaceholder;` |
| `SendButtonText: string` | `string` | `__property UnicodeString SendButtonText;` |
| `SendButtonStyle: TsgcHTMLButtonStyle` | [TsgcHTMLButtonStyle](../types/TsgcHTMLButtonStyle.md) | `__property TsgcHTMLButtonStyle * SendButtonStyle;` |
| `ShowTypingIndicator: Boolean` | `Boolean` | `__property bool ShowTypingIndicator;` |
| `TypingText: string` | `string` | `__property UnicodeString TypingText;` |
| `Title: string` | `string` | `__property UnicodeString Title;` |
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
procedure AddMessage(const aSender, aText: string; aAlign: TsgcHTMLChatAlign = caLeft; aColor: TsgcHTMLColor = hcPrimary; const aTimestamp: string = '');
function GetLastMessageHTML: string;
```

C++Builder

```cpp
void __fastcall AddMessage(const UnicodeString aSender, const UnicodeString aText, TsgcHTMLChatAlign * aAlign = caLeft, TsgcHTMLColor * aColor = hcPrimary, const UnicodeString aTimestamp = '');
UnicodeString __fastcall GetLastMessageHTML();
```

