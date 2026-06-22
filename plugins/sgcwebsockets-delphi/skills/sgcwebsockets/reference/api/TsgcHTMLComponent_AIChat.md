# TsgcHTMLComponent_AIChat

unit: sgcHTML_Component_AIChat
Edition: All-Access

Add `sgcHTML_Component_AIChat` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `StreamingActive: Boolean (read-only)` | `Boolean` | `__property bool StreamingActive /* read-only */;` |
| `AIProvider: TsgcHTMLAIProvider` | [TsgcHTMLAIProvider](../types/TsgcHTMLAIProvider.md) | `__property TsgcHTMLAIProvider * AIProvider;` |
| `ModelName: string` | `string` | `__property UnicodeString ModelName;` |
| `ShowModelSelector: Boolean` | `Boolean` | `__property bool ShowModelSelector;` |
| `SystemPrompt: string` | `string` | `__property UnicodeString SystemPrompt;` |
| `StreamingEnabled: Boolean` | `Boolean` | `__property bool StreamingEnabled;` |
| `AIChatID: string` | `string` | `__property UnicodeString AIChatID;` |
| `WelcomeMessage: string` | `string` | `__property UnicodeString WelcomeMessage;` |
| `UserColor: TsgcHTMLColor` | [TsgcHTMLColor](../types/TsgcHTMLColor.md) | `__property TsgcHTMLColor * UserColor;` |
| `AIColor: TsgcHTMLColor` | [TsgcHTMLColor](../types/TsgcHTMLColor.md) | `__property TsgcHTMLColor * AIColor;` |
| `AIName: string` | `string` | `__property UnicodeString AIName;` |
| `RAGEnabled: Boolean` | `Boolean` | `__property bool RAGEnabled;` |
| `RAGDisplayMode: TsgcRAGDisplayMode` | [TsgcRAGDisplayMode](../types/TsgcRAGDisplayMode.md) | `__property TsgcRAGDisplayMode * RAGDisplayMode;` |
| `RAGLabel: string` | `string` | `__property UnicodeString RAGLabel;` |
| `ShowSourceReferences: Boolean` | `Boolean` | `__property bool ShowSourceReferences;` |
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
| `OnRAGContext: TsgcAIChatRAGContextEvent` | [TsgcAIChatRAGContextEvent](../types/TsgcAIChatRAGContextEvent.md) | `__property TsgcAIChatRAGContextEvent OnRAGContext;` |
| `OnChatSend: TsgcAIChatSendEvent` | [TsgcAIChatSendEvent](../types/TsgcAIChatSendEvent.md) | `__property TsgcAIChatSendEvent OnChatSend;` |
| `OnDataChanged: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDataChanged;` |
| `OnBeforeRefresh: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnBeforeRefresh;` |
| `OnAfterRefresh: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAfterRefresh;` |

## Methods

Delphi

```pascal
procedure AddUserMessage(const aText: string);
procedure AddAIMessage(const aText: string);
procedure AddStreamChunk(const aText: string);
procedure BeginStreaming;
procedure PushStreamChunk(const aChunk: string);
procedure EndStreaming;
function GetStreamFragmentHTML: string;
procedure ProcessUserMessage(const aMessage: string);
procedure AddAIMessageWithSources(const aText, aSourcesHTML: string);
function GetConversationHistoryJSON: string;
procedure AddMessage(const aSender, aText: string; aAlign: TsgcHTMLChatAlign = caLeft; aColor: TsgcHTMLColor = hcPrimary; const aTimestamp: string = '');
function GetLastMessageHTML: string;
```

C++Builder

```cpp
void __fastcall AddUserMessage(const UnicodeString aText);
void __fastcall AddAIMessage(const UnicodeString aText);
void __fastcall AddStreamChunk(const UnicodeString aText);
void __fastcall BeginStreaming();
void __fastcall PushStreamChunk(const UnicodeString aChunk);
void __fastcall EndStreaming();
UnicodeString __fastcall GetStreamFragmentHTML();
void __fastcall ProcessUserMessage(const UnicodeString aMessage);
void __fastcall AddAIMessageWithSources(const UnicodeString aText, const UnicodeString aSourcesHTML);
UnicodeString __fastcall GetConversationHistoryJSON();
void __fastcall AddMessage(const UnicodeString aSender, const UnicodeString aText, TsgcHTMLChatAlign * aAlign = caLeft, TsgcHTMLColor * aColor = hcPrimary, const UnicodeString aTimestamp = '');
UnicodeString __fastcall GetLastMessageHTML();
```

