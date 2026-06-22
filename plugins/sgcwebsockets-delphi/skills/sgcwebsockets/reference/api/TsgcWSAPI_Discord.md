# TsgcWSAPI_Discord

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `DiscordOptions: TsgcWSDiscord_Options` | [TsgcWSDiscord_Options](../types/TsgcWSDiscord_Options.md) | `__property TsgcWSDiscord_Options * DiscordOptions;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `Session_Id: String (read-only)` | `String` | `__property UnicodeString Session_Id /* read-only */;` |
| `Sequence: Integer (read-only)` | `Integer` | `__property int Sequence /* read-only */;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDiscordBeforeReconnect: TsgcWSDiscordDBeforeReconnectEvent` | [TsgcWSDiscordDBeforeReconnectEvent](../types/TsgcWSDiscordDBeforeReconnectEvent.md) | `__property TsgcWSDiscordDBeforeReconnectEvent OnDiscordBeforeReconnect;` |
| `OnDiscordReady: TsgcWSDiscordReadyEvent` | [TsgcWSDiscordReadyEvent](../types/TsgcWSDiscordReadyEvent.md) | `__property TsgcWSDiscordReadyEvent OnDiscordReady;` |
| `OnDiscordResumed: TsgcWSDiscordResumedEvent` | [TsgcWSDiscordResumedEvent](../types/TsgcWSDiscordResumedEvent.md) | `__property TsgcWSDiscordResumedEvent OnDiscordResumed;` |
| `OnDiscordDispatch: TsgcWSDiscordDispatchEvent` | [TsgcWSDiscordDispatchEvent](../types/TsgcWSDiscordDispatchEvent.md) | `__property TsgcWSDiscordDispatchEvent OnDiscordDispatch;` |
| `OnDiscordEvent: TsgcWSDiscordEvent` | [TsgcWSDiscordEvent](../types/TsgcWSDiscordEvent.md) | `__property TsgcWSDiscordEvent OnDiscordEvent;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure Ping;
function GET_Request(const aPath: String): string;
function POST_Request(const aPath, aMessage: String): string;
function PUT_Request(const aPath, aMessage: String): string;
function PATCH_Request(const aPath, aMessage: String): string;
function DELETE_Request(const aPath: String): string;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Ping();
UnicodeString __fastcall GET_Request(const UnicodeString aPath);
UnicodeString __fastcall POST_Request(const UnicodeString aPath, const UnicodeString aMessage);
UnicodeString __fastcall PUT_Request(const UnicodeString aPath, const UnicodeString aMessage);
UnicodeString __fastcall PATCH_Request(const UnicodeString aPath, const UnicodeString aMessage);
UnicodeString __fastcall DELETE_Request(const UnicodeString aPath);
void __fastcall QueueClear();
```

