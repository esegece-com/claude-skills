# TsgcAIChat

unit: sgcAI
Edition: Enterprise

Add `sgcAI` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Provider: TsgcAIChatProvider` | [TsgcAIChatProvider](../types/TsgcAIChatProvider.md) | `__property TsgcAIChatProvider * Provider;` |
| `ChatOptions: TsgcAIChatOptions` | [TsgcAIChatOptions](../types/TsgcAIChatOptions.md) | `__property TsgcAIChatOptions * ChatOptions;` |
| `MaxHistoryMessages: Integer` | `Integer` | `__property int MaxHistoryMessages;` |
| `SystemMessage: string` | `string` | `__property UnicodeString SystemMessage;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnChatMessage: TsgcAIChatMessageEvent` | [TsgcAIChatMessageEvent](../types/TsgcAIChatMessageEvent.md) | `__property TsgcAIChatMessageEvent OnChatMessage;` |
| `OnChatStream: TsgcAIChatStreamEvent` | [TsgcAIChatStreamEvent](../types/TsgcAIChatStreamEvent.md) | `__property TsgcAIChatStreamEvent OnChatStream;` |
| `OnChatError: TsgcAIChatErrorEvent` | [TsgcAIChatErrorEvent](../types/TsgcAIChatErrorEvent.md) | `__property TsgcAIChatErrorEvent OnChatError;` |

## Methods

Delphi

```pascal
function Chat(const aMessage: string): string;
function ChatStream(const aMessage: string): string;
function ChatWithSystem(const aSystem, aMessage: string): string;
procedure ClearHistory;
function GetHistory: TsgcAIChatHistory;
```

C++Builder

```cpp
UnicodeString __fastcall Chat(const UnicodeString aMessage);
UnicodeString __fastcall ChatStream(const UnicodeString aMessage);
UnicodeString __fastcall ChatWithSystem(const UnicodeString aSystem, const UnicodeString aMessage);
void __fastcall ClearHistory();
TsgcAIChatHistory * __fastcall GetHistory();
```

