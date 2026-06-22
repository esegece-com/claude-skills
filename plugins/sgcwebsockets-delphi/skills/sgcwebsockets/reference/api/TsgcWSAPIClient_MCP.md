# TsgcWSAPIClient_MCP

unit: sgcAI
Edition: requires SGC_AI_MCP

Add `sgcAI` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `MCPOptions: TsgcAI_MCP_Client_Options` | [TsgcAI_MCP_Client_Options](../types/TsgcAI_MCP_Client_Options.md) | `__property TsgcAI_MCP_Client_Options * MCPOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `Session: TsgcAI_MCP_Session_Type (read-only)` | [TsgcAI_MCP_Session_Type](../types/TsgcAI_MCP_Session_Type.md) | `__property TsgcAI_MCP_Session_Type * Session /* read-only */;` |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnMCPInitialize: TsgcAI_MCP_Client_OnInitializeEvent` | [TsgcAI_MCP_Client_OnInitializeEvent](../types/TsgcAI_MCP_Client_OnInitializeEvent.md) | `__property TsgcAI_MCP_Client_OnInitializeEvent OnMCPInitialize;` |
| `OnMCPPing: TsgcAI_MCP_Client_OnPingEvent` | [TsgcAI_MCP_Client_OnPingEvent](../types/TsgcAI_MCP_Client_OnPingEvent.md) | `__property TsgcAI_MCP_Client_OnPingEvent OnMCPPing;` |
| `OnMCPListTools: TsgcAI_MCP_Client_OnListToolsEvent` | [TsgcAI_MCP_Client_OnListToolsEvent](../types/TsgcAI_MCP_Client_OnListToolsEvent.md) | `__property TsgcAI_MCP_Client_OnListToolsEvent OnMCPListTools;` |
| `OnMCPResponseTool: TsgcAI_MCP_Client_OnResponseToolEvent` | [TsgcAI_MCP_Client_OnResponseToolEvent](../types/TsgcAI_MCP_Client_OnResponseToolEvent.md) | `__property TsgcAI_MCP_Client_OnResponseToolEvent OnMCPResponseTool;` |
| `OnMCPListPrompts: TsgcAI_MCP_Client_OnListPromptsEvent` | [TsgcAI_MCP_Client_OnListPromptsEvent](../types/TsgcAI_MCP_Client_OnListPromptsEvent.md) | `__property TsgcAI_MCP_Client_OnListPromptsEvent OnMCPListPrompts;` |
| `OnMCPResponsePrompt: TsgcAI_MCP_Client_OnResponsePromptEvent` | [TsgcAI_MCP_Client_OnResponsePromptEvent](../types/TsgcAI_MCP_Client_OnResponsePromptEvent.md) | `__property TsgcAI_MCP_Client_OnResponsePromptEvent OnMCPResponsePrompt;` |
| `OnMCPListResources: TsgcAI_MCP_Client_OnListResourcesEvent` | [TsgcAI_MCP_Client_OnListResourcesEvent](../types/TsgcAI_MCP_Client_OnListResourcesEvent.md) | `__property TsgcAI_MCP_Client_OnListResourcesEvent OnMCPListResources;` |
| `OnMCPResponseResource: TsgcAI_MCP_Client_OnResponseResourceEvent` | [TsgcAI_MCP_Client_OnResponseResourceEvent](../types/TsgcAI_MCP_Client_OnResponseResourceEvent.md) | `__property TsgcAI_MCP_Client_OnResponseResourceEvent OnMCPResponseResource;` |
| `OnMCPListRoots: TsgcAI_MCP_Client_OnListRootsEvent` | [TsgcAI_MCP_Client_OnListRootsEvent](../types/TsgcAI_MCP_Client_OnListRootsEvent.md) | `__property TsgcAI_MCP_Client_OnListRootsEvent OnMCPListRoots;` |
| `OnMCPSamplingCreateMessage: TsgcAI_MCP_Client_OnSamplingCreateMessageEvent` | [TsgcAI_MCP_Client_OnSamplingCreateMessageEvent](../types/TsgcAI_MCP_Client_OnSamplingCreateMessageEvent.md) | `__property TsgcAI_MCP_Client_OnSamplingCreateMessageEvent OnMCPSamplingCreateMessage;` |
| `OnMCPElicitationCreate: TsgcAI_MCP_Client_OnElicitationCreateEvent` | [TsgcAI_MCP_Client_OnElicitationCreateEvent](../types/TsgcAI_MCP_Client_OnElicitationCreateEvent.md) | `__property TsgcAI_MCP_Client_OnElicitationCreateEvent OnMCPElicitationCreate;` |
| `OnMCPStreamMessage: TsgcAI_MCP_Client_OnStreamMessageEvent` | [TsgcAI_MCP_Client_OnStreamMessageEvent](../types/TsgcAI_MCP_Client_OnStreamMessageEvent.md) | `__property TsgcAI_MCP_Client_OnStreamMessageEvent OnMCPStreamMessage;` |
| `OnMCPListResourceTemplates: TsgcAI_MCP_Client_OnListResourceTemplatesEvent` | [TsgcAI_MCP_Client_OnListResourceTemplatesEvent](../types/TsgcAI_MCP_Client_OnListResourceTemplatesEvent.md) | `__property TsgcAI_MCP_Client_OnListResourceTemplatesEvent OnMCPListResourceTemplates;` |
| `OnMCPLoggingMessage: TsgcAI_MCP_Client_OnLoggingMessageEvent` | [TsgcAI_MCP_Client_OnLoggingMessageEvent](../types/TsgcAI_MCP_Client_OnLoggingMessageEvent.md) | `__property TsgcAI_MCP_Client_OnLoggingMessageEvent OnMCPLoggingMessage;` |
| `OnMCPCompletionComplete: TsgcAI_MCP_Client_OnCompletionCompleteEvent` | [TsgcAI_MCP_Client_OnCompletionCompleteEvent](../types/TsgcAI_MCP_Client_OnCompletionCompleteEvent.md) | `__property TsgcAI_MCP_Client_OnCompletionCompleteEvent OnMCPCompletionComplete;` |
| `OnMCPProgress: TsgcAI_MCP_Client_OnProgressEvent` | [TsgcAI_MCP_Client_OnProgressEvent](../types/TsgcAI_MCP_Client_OnProgressEvent.md) | `__property TsgcAI_MCP_Client_OnProgressEvent OnMCPProgress;` |
| `OnMCPResourcesUpdated: TsgcAI_MCP_Client_OnResourcesUpdatedEvent` | [TsgcAI_MCP_Client_OnResourcesUpdatedEvent](../types/TsgcAI_MCP_Client_OnResourcesUpdatedEvent.md) | `__property TsgcAI_MCP_Client_OnResourcesUpdatedEvent OnMCPResourcesUpdated;` |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
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
function Initialize: Boolean;
procedure ListTools(const aCursor: string = '');
procedure RequestTool(const aName: string; const aArguments: IsgcJSON = nil);
procedure ListPrompts(const aCursor: string = '');
procedure RequestPrompt(const aName: string; const aArguments: IsgcJSON = nil);
procedure ListResources(const aCursor: string = '');
procedure RequestResource(const aUri: string);
procedure ListResourceTemplates(const aCursor: string = '');
procedure SubscribeResource(const aUri: string);
procedure UnsubscribeResource(const aUri: string);
procedure SetLoggingLevel(aLevel: TsgcAI_MCP_LoggingLevel);
procedure Complete(const aRefType, aRefName, aArgumentName, aArgumentValue: string);
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Ping();
bool __fastcall Initialize();
void __fastcall ListTools(const UnicodeString aCursor = '');
void __fastcall RequestTool(const UnicodeString aName, const IsgcJSON aArguments = nil);
void __fastcall ListPrompts(const UnicodeString aCursor = '');
void __fastcall RequestPrompt(const UnicodeString aName, const IsgcJSON aArguments = nil);
void __fastcall ListResources(const UnicodeString aCursor = '');
void __fastcall RequestResource(const UnicodeString aUri);
void __fastcall ListResourceTemplates(const UnicodeString aCursor = '');
void __fastcall SubscribeResource(const UnicodeString aUri);
void __fastcall UnsubscribeResource(const UnicodeString aUri);
void __fastcall SetLoggingLevel(TsgcAI_MCP_LoggingLevel * aLevel);
void __fastcall Complete(const UnicodeString aRefType, const UnicodeString aRefName, const UnicodeString aArgumentName, const UnicodeString aArgumentValue);
void __fastcall QueueClear();
```

