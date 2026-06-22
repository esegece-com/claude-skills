# TsgcWSAPIServer_MCP

unit: sgcAI
Edition: requires SGC_AI_MCP

Add `sgcAI` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `MCPOptions: TsgcAI_MCP_Server_Options` | [TsgcAI_MCP_Server_Options](../types/TsgcAI_MCP_Server_Options.md) | `__property TsgcAI_MCP_Server_Options * MCPOptions;` |
| `EndpointOptions: TsgcWSMCPServerEndpoint_Options` | [TsgcWSMCPServerEndpoint_Options](../types/TsgcWSMCPServerEndpoint_Options.md) | `__property TsgcWSMCPServerEndpoint_Options * EndpointOptions;` |
| `TransportOptions: TsgcWSMCPServerTransport_Options` | [TsgcWSMCPServerTransport_Options](../types/TsgcWSMCPServerTransport_Options.md) | `__property TsgcWSMCPServerTransport_Options * TransportOptions;` |
| `Server: TsgcWSComponent_Server` | [TsgcWSComponent_Server](../types/TsgcWSComponent_Server.md) | `__property TsgcWSComponent_Server * Server;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `Tools: TsgcAI_MCP_ToolsList (read-only)` | [TsgcAI_MCP_ToolsList](../types/TsgcAI_MCP_ToolsList.md) | `__property TsgcAI_MCP_ToolsList * Tools /* read-only */;` |
| `Prompts: TsgcAI_MCP_PromptsList (read-only)` | [TsgcAI_MCP_PromptsList](../types/TsgcAI_MCP_PromptsList.md) | `__property TsgcAI_MCP_PromptsList * Prompts /* read-only */;` |
| `Resources: TsgcAI_MCP_ResourcesList (read-only)` | [TsgcAI_MCP_ResourcesList](../types/TsgcAI_MCP_ResourcesList.md) | `__property TsgcAI_MCP_ResourcesList * Resources /* read-only */;` |
| `ResourceTemplates: TsgcAI_MCP_ResourceTemplatesList (read-only)` | [TsgcAI_MCP_ResourceTemplatesList](../types/TsgcAI_MCP_ResourceTemplatesList.md) | `__property TsgcAI_MCP_ResourceTemplatesList * ResourceTemplates /* read-only */;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnMCPException: TsgcMCPServerOnExceptionEvent` | [TsgcMCPServerOnExceptionEvent](../types/TsgcMCPServerOnExceptionEvent.md) | `__property TsgcMCPServerOnExceptionEvent OnMCPException;` |
| `OnMCPInitialize: TsgcAI_MCP_Server_OnInitializeEvent` | [TsgcAI_MCP_Server_OnInitializeEvent](../types/TsgcAI_MCP_Server_OnInitializeEvent.md) | `__property TsgcAI_MCP_Server_OnInitializeEvent OnMCPInitialize;` |
| `OnMCPSessionNew: TsgcAI_MCP_Server_OnSessionNewEvent` | [TsgcAI_MCP_Server_OnSessionNewEvent](../types/TsgcAI_MCP_Server_OnSessionNewEvent.md) | `__property TsgcAI_MCP_Server_OnSessionNewEvent OnMCPSessionNew;` |
| `OnMCPSessionEnd: TsgcAI_MCP_Server_OnSessionEndEvent` | [TsgcAI_MCP_Server_OnSessionEndEvent](../types/TsgcAI_MCP_Server_OnSessionEndEvent.md) | `__property TsgcAI_MCP_Server_OnSessionEndEvent OnMCPSessionEnd;` |
| `OnMCPRequestTool: TsgcAI_MCP_Server_OnRequestToolEvent` | [TsgcAI_MCP_Server_OnRequestToolEvent](../types/TsgcAI_MCP_Server_OnRequestToolEvent.md) | `__property TsgcAI_MCP_Server_OnRequestToolEvent OnMCPRequestTool;` |
| `OnMCPRequestPrompt: TsgcAI_MCP_Server_OnRequestPromptEvent` | [TsgcAI_MCP_Server_OnRequestPromptEvent](../types/TsgcAI_MCP_Server_OnRequestPromptEvent.md) | `__property TsgcAI_MCP_Server_OnRequestPromptEvent OnMCPRequestPrompt;` |
| `OnMCPRequestResource: TsgcAI_MCP_Server_OnRequestResourceEvent` | [TsgcAI_MCP_Server_OnRequestResourceEvent](../types/TsgcAI_MCP_Server_OnRequestResourceEvent.md) | `__property TsgcAI_MCP_Server_OnRequestResourceEvent OnMCPRequestResource;` |
| `OnMCPResponseRootsList: TsgcAI_MCP_Server_OnResponseRootsListEvent` | [TsgcAI_MCP_Server_OnResponseRootsListEvent](../types/TsgcAI_MCP_Server_OnResponseRootsListEvent.md) | `__property TsgcAI_MCP_Server_OnResponseRootsListEvent OnMCPResponseRootsList;` |
| `OnMCPResponseSamplingCreateMessage: TsgcAI_MCP_Server_OnResponseSamplingCreateMessageEvent` | [TsgcAI_MCP_Server_OnResponseSamplingCreateMessageEvent](../types/TsgcAI_MCP_Server_OnResponseSamplingCreateMessageEvent.md) | `__property TsgcAI_MCP_Server_OnResponseSamplingCreateMessageEvent OnMCPResponseSamplingCreateMessage;` |
| `OnMCPResponseElicitationCreate: TsgcAI_MCP_Server_OnResponseElicitationCreateMessageEvent` | [TsgcAI_MCP_Server_OnResponseElicitationCreateMessageEvent](../types/TsgcAI_MCP_Server_OnResponseElicitationCreateMessageEvent.md) | `__property TsgcAI_MCP_Server_OnResponseElicitationCreateMessageEvent OnMCPResponseElicitationCreate;` |
| `OnMCPHTTPRequest: TsgcMCPServerOnHTTPRequestEvent` | [TsgcMCPServerOnHTTPRequestEvent](../types/TsgcMCPServerOnHTTPRequestEvent.md) | `__property TsgcMCPServerOnHTTPRequestEvent OnMCPHTTPRequest;` |
| `OnMCPHTTPResponse: TsgcMCPServerOnHTTPResponseEvent` | [TsgcMCPServerOnHTTPResponseEvent](../types/TsgcMCPServerOnHTTPResponseEvent.md) | `__property TsgcMCPServerOnHTTPResponseEvent OnMCPHTTPResponse;` |
| `OnMCPRequestResourceTemplatesList: TsgcAI_MCP_Server_OnRequestResourceTemplatesListEvent` | [TsgcAI_MCP_Server_OnRequestResourceTemplatesListEvent](../types/TsgcAI_MCP_Server_OnRequestResourceTemplatesListEvent.md) | `__property TsgcAI_MCP_Server_OnRequestResourceTemplatesListEvent OnMCPRequestResourceTemplatesList;` |
| `OnMCPResourceSubscribe: TsgcAI_MCP_Server_OnResourceSubscribeEvent` | [TsgcAI_MCP_Server_OnResourceSubscribeEvent](../types/TsgcAI_MCP_Server_OnResourceSubscribeEvent.md) | `__property TsgcAI_MCP_Server_OnResourceSubscribeEvent OnMCPResourceSubscribe;` |
| `OnMCPResourceUnsubscribe: TsgcAI_MCP_Server_OnResourceUnsubscribeEvent` | [TsgcAI_MCP_Server_OnResourceUnsubscribeEvent](../types/TsgcAI_MCP_Server_OnResourceUnsubscribeEvent.md) | `__property TsgcAI_MCP_Server_OnResourceUnsubscribeEvent OnMCPResourceUnsubscribe;` |
| `OnMCPLoggingSetLevel: TsgcAI_MCP_Server_OnLoggingSetLevelEvent` | [TsgcAI_MCP_Server_OnLoggingSetLevelEvent](../types/TsgcAI_MCP_Server_OnLoggingSetLevelEvent.md) | `__property TsgcAI_MCP_Server_OnLoggingSetLevelEvent OnMCPLoggingSetLevel;` |
| `OnMCPCompletionComplete: TsgcAI_MCP_Server_OnCompletionCompleteEvent` | [TsgcAI_MCP_Server_OnCompletionCompleteEvent](../types/TsgcAI_MCP_Server_OnCompletionCompleteEvent.md) | `__property TsgcAI_MCP_Server_OnCompletionCompleteEvent OnMCPCompletionComplete;` |
| `OnMCPProgress: TsgcAI_MCP_Server_OnProgressEvent` | [TsgcAI_MCP_Server_OnProgressEvent](../types/TsgcAI_MCP_Server_OnProgressEvent.md) | `__property TsgcAI_MCP_Server_OnProgressEvent OnMCPProgress;` |
| `OnMCPCancelled: TsgcAI_MCP_Server_OnCancelledEvent` | [TsgcAI_MCP_Server_OnCancelledEvent](../types/TsgcAI_MCP_Server_OnCancelledEvent.md) | `__property TsgcAI_MCP_Server_OnCancelledEvent OnMCPCancelled;` |
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
function RequestRootsList(const aSessionId: string): Boolean;
function RequestSamplingCreateMessage(const aSessionId: string; const aRequest: TsgcAI_MCP_Request_SamplingCreateMessage): Boolean;
function RequestElicitationCreate(const aSessionId: string; const aRequest: TsgcAI_MCP_Request_ElicitationCreate): Boolean;
procedure SendNotificationToolsListChanged;
procedure SendNotificationPromptsListChanged;
procedure SendNotificationResourcesListChanged;
procedure SendNotificationResourcesUpdated(const aUri: string);
procedure SendLogMessage(aLevel: TsgcAI_MCP_LoggingLevel; const aLogger, aData: string);
procedure KeepAlive(const aConnection: TsgcWSConnection; const aMessage: string);
procedure QueueClear;
```

C++Builder

```cpp
bool __fastcall RequestRootsList(const UnicodeString aSessionId);
bool __fastcall RequestSamplingCreateMessage(const UnicodeString aSessionId, const TsgcAI_MCP_Request_SamplingCreateMessage * aRequest);
bool __fastcall RequestElicitationCreate(const UnicodeString aSessionId, const TsgcAI_MCP_Request_ElicitationCreate * aRequest);
void __fastcall SendNotificationToolsListChanged();
void __fastcall SendNotificationPromptsListChanged();
void __fastcall SendNotificationResourcesListChanged();
void __fastcall SendNotificationResourcesUpdated(const UnicodeString aUri);
void __fastcall SendLogMessage(TsgcAI_MCP_LoggingLevel * aLevel, const UnicodeString aLogger, const UnicodeString aData);
void __fastcall KeepAlive(const TsgcWSConnection * aConnection, const UnicodeString aMessage);
void __fastcall QueueClear();
```

