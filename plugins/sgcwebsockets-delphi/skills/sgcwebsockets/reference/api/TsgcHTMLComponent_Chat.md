# TsgcHTMLComponent_Chat

unit: sgcHTML_Component_Chat

Add `sgcHTML_Component_Chat` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Messages: TsgcHTMLChat_Messages` | [TsgcHTMLChat_Messages](../types/TsgcHTMLChat_Messages.md) | `__property TsgcHTMLChat_Messages * Messages;` |
| `Options: TsgcHTMLChat_Options` | [TsgcHTMLChat_Options](../types/TsgcHTMLChat_Options.md) | `__property TsgcHTMLChat_Options * Options;` |
| `ChatID: string` | `string` | `__property UnicodeString ChatID;` |
| `Height: string` | `string` | `__property UnicodeString Height;` |
| `Title: string` | `string` | `__property UnicodeString Title;` |
| `Subtitle: string` | `string` | `__property UnicodeString Subtitle;` |
| `HeaderAvatarURL: string` | `string` | `__property UnicodeString HeaderAvatarURL;` |
| `HeaderAvatarInitials: string` | `string` | `__property UnicodeString HeaderAvatarInitials;` |
| `ShowInput: Boolean` | `Boolean` | `__property bool ShowInput;` |
| `InputPlaceholder: string` | `string` | `__property UnicodeString InputPlaceholder;` |
| `ShowAttachButton: Boolean` | `Boolean` | `__property bool ShowAttachButton;` |
| `ShowEmojiButton: Boolean` | `Boolean` | `__property bool ShowEmojiButton;` |
| `ShowTypingIndicator: Boolean` | `Boolean` | `__property bool ShowTypingIndicator;` |
| `TypingText: string` | `string` | `__property UnicodeString TypingText;` |
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
| `OnSendMessage: TsgcHTMLChat_SendEvent` | [TsgcHTMLChat_SendEvent](../types/TsgcHTMLChat_SendEvent.md) | `__property TsgcHTMLChat_SendEvent OnSendMessage;` |
| `OnMediaClick: TsgcHTMLChat_MediaClickEvent` | [TsgcHTMLChat_MediaClickEvent](../types/TsgcHTMLChat_MediaClickEvent.md) | `__property TsgcHTMLChat_MediaClickEvent OnMediaClick;` |
| `OnDataChanged: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDataChanged;` |
| `OnBeforeRefresh: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnBeforeRefresh;` |
| `OnAfterRefresh: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAfterRefresh;` |

## Methods

Delphi

```pascal
procedure AddMessage(const aSender, aText: string; aAlign: TsgcHTMLChatMessageAlign = maLeft; aColor: TsgcHTMLColor = hcPrimary; const aTimestamp: string = '');
procedure AddImageMessage(const aSender, aMediaURL: string; aAlign: TsgcHTMLChatMessageAlign = maLeft; aColor: TsgcHTMLColor = hcPrimary; const aCaption: string = ''; const aTimestamp: string = '');
procedure AddFileMessage(const aSender, aMediaURL, aFileName, aFileSize: string; aAlign: TsgcHTMLChatMessageAlign = maLeft; aColor: TsgcHTMLColor = hcPrimary; const aTimestamp: string = '');
procedure AddSystemMessage(const aText: string; const aTimestamp: string = '');
function GetLastMessageHTML: string;
```

C++Builder

```cpp
void __fastcall AddMessage(const UnicodeString aSender, const UnicodeString aText, TsgcHTMLChatMessageAlign * aAlign = maLeft, TsgcHTMLColor * aColor = hcPrimary, const UnicodeString aTimestamp = '');
void __fastcall AddImageMessage(const UnicodeString aSender, const UnicodeString aMediaURL, TsgcHTMLChatMessageAlign * aAlign = maLeft, TsgcHTMLColor * aColor = hcPrimary, const UnicodeString aCaption = '', const UnicodeString aTimestamp = '');
void __fastcall AddFileMessage(const UnicodeString aSender, const UnicodeString aMediaURL, const UnicodeString aFileName, const UnicodeString aFileSize, TsgcHTMLChatMessageAlign * aAlign = maLeft, TsgcHTMLColor * aColor = hcPrimary, const UnicodeString aTimestamp = '');
void __fastcall AddSystemMessage(const UnicodeString aText, const UnicodeString aTimestamp = '');
UnicodeString __fastcall GetLastMessageHTML();
```

