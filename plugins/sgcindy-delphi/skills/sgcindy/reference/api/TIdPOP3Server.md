# TIdPOP3Server

unit: IdPOP3Server

Add `IdPOP3Server` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `DefaultPort: TIdPort` | `TIdPort` | `__property TIdPort * DefaultPort;` |
| `UseTLS: TIdUseTLS` | [TIdUseTLS](../types/TIdUseTLS.md) | `__property TIdUseTLS * UseTLS;` |
| `CommandHandlers: TIdCommandHandlers` | [TIdCommandHandlers](../types/TIdCommandHandlers.md) | `__property TIdCommandHandlers * CommandHandlers;` |
| `ExceptionReply: TIdReply` | [TIdReply](../types/TIdReply.md) | `__property TIdReply * ExceptionReply;` |
| `Greeting: TIdReply` | [TIdReply](../types/TIdReply.md) | `__property TIdReply * Greeting;` |
| `HelpReply: TIdReply` | [TIdReply](../types/TIdReply.md) | `__property TIdReply * HelpReply;` |
| `MaxConnectionReply: TIdReply` | [TIdReply](../types/TIdReply.md) | `__property TIdReply * MaxConnectionReply;` |
| `ReplyTexts: TIdReplies` | [TIdReplies](../types/TIdReplies.md) | `__property TIdReplies * ReplyTexts;` |
| `ReplyUnknownCommand: TIdReply` | [TIdReply](../types/TIdReply.md) | `__property TIdReply * ReplyUnknownCommand;` |
| `Contexts: TIdContextThreadList (read-only)` | `TIdContextThreadList` | `__property TIdContextThreadList * Contexts /* read-only */;` |
| `ContextClass: TIdServerContextClass` | [TIdServerContextClass](../types/TIdServerContextClass.md) | `__property TIdServerContextClass * ContextClass;` |
| `ImplicitIOHandler: Boolean (read-only)` | `Boolean` | `__property bool ImplicitIOHandler /* read-only */;` |
| `ImplicitScheduler: Boolean (read-only)` | `Boolean` | `__property bool ImplicitScheduler /* read-only */;` |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `Bindings: TIdSocketHandles` | [TIdSocketHandles](../types/TIdSocketHandles.md) | `__property TIdSocketHandles * Bindings;` |
| `Intercept: TIdServerIntercept` | [TIdServerIntercept](../types/TIdServerIntercept.md) | `__property TIdServerIntercept * Intercept;` |
| `IOHandler: TIdServerIOHandler` | [TIdServerIOHandler](../types/TIdServerIOHandler.md) | `__property TIdServerIOHandler * IOHandler;` |
| `ListenQueue: integer` | `integer` | `__property int ListenQueue;` |
| `MaxConnections: Integer` | `Integer` | `__property int MaxConnections;` |
| `ReuseSocket: TIdReuseSocket` | [TIdReuseSocket](../types/TIdReuseSocket.md) | `__property TIdReuseSocket * ReuseSocket;` |
| `UseNagle: boolean` | `boolean` | `__property bool UseNagle;` |
| `TerminateWaitTime: Integer` | `Integer` | `__property int TerminateWaitTime;` |
| `Scheduler: TIdScheduler` | [TIdScheduler](../types/TIdScheduler.md) | `__property TIdScheduler * Scheduler;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnCheckUser: TIdPOP3ServerLogin` | [TIdPOP3ServerLogin](../types/TIdPOP3ServerLogin.md) | `__property TIdPOP3ServerLogin * OnCheckUser;` |
| `OnList: TIdPOP3ServerMessageNumberEvent` | [TIdPOP3ServerMessageNumberEvent](../types/TIdPOP3ServerMessageNumberEvent.md) | `__property TIdPOP3ServerMessageNumberEvent OnList;` |
| `OnRetrieve: TIdPOP3ServerMessageNumberEvent` | [TIdPOP3ServerMessageNumberEvent](../types/TIdPOP3ServerMessageNumberEvent.md) | `__property TIdPOP3ServerMessageNumberEvent OnRetrieve;` |
| `OnDelete: TIdPOP3ServerMessageNumberEvent` | [TIdPOP3ServerMessageNumberEvent](../types/TIdPOP3ServerMessageNumberEvent.md) | `__property TIdPOP3ServerMessageNumberEvent OnDelete;` |
| `OnUIDL: TIdPOP3ServerMessageNumberEvent` | [TIdPOP3ServerMessageNumberEvent](../types/TIdPOP3ServerMessageNumberEvent.md) | `__property TIdPOP3ServerMessageNumberEvent OnUIDL;` |
| `OnStat: TIdPOP3ServerStatEvent` | [TIdPOP3ServerStatEvent](../types/TIdPOP3ServerStatEvent.md) | `__property TIdPOP3ServerStatEvent OnStat;` |
| `OnTop: TIdPOP3ServerTOPCommandEvent` | [TIdPOP3ServerTOPCommandEvent](../types/TIdPOP3ServerTOPCommandEvent.md) | `__property TIdPOP3ServerTOPCommandEvent OnTop;` |
| `OnReset: TIdPOP3ServerNoParamEvent` | [TIdPOP3ServerNoParamEvent](../types/TIdPOP3ServerNoParamEvent.md) | `__property TIdPOP3ServerNoParamEvent OnReset;` |
| `OnQuit: TIdPOP3ServerNoParamEvent` | [TIdPOP3ServerNoParamEvent](../types/TIdPOP3ServerNoParamEvent.md) | `__property TIdPOP3ServerNoParamEvent OnQuit;` |
| `OnAPOP: TIdPOP3ServerAPOPCommandEvent` | [TIdPOP3ServerAPOPCommandEvent](../types/TIdPOP3ServerAPOPCommandEvent.md) | `__property TIdPOP3ServerAPOPCommandEvent OnAPOP;` |
| `OnCAPA: TIdPOP3ServerCAPACommandEvent` | [TIdPOP3ServerCAPACommandEvent](../types/TIdPOP3ServerCAPACommandEvent.md) | `__property TIdPOP3ServerCAPACommandEvent OnCAPA;` |
| `OnAfterCommandHandler: TIdCmdTCPServerAfterCommandHandlerEvent` | [TIdCmdTCPServerAfterCommandHandlerEvent](../types/TIdCmdTCPServerAfterCommandHandlerEvent.md) | `__property TIdCmdTCPServerAfterCommandHandlerEvent OnAfterCommandHandler;` |
| `OnBeforeCommandHandler: TIdCmdTCPServerBeforeCommandHandlerEvent` | [TIdCmdTCPServerBeforeCommandHandlerEvent](../types/TIdCmdTCPServerBeforeCommandHandlerEvent.md) | `__property TIdCmdTCPServerBeforeCommandHandlerEvent OnBeforeCommandHandler;` |
| `OnExecute: TIdServerThreadEvent` | [TIdServerThreadEvent](../types/TIdServerThreadEvent.md) | `__property TIdServerThreadEvent OnExecute;` |
| `OnBeforeBind: TIdSocketHandleEvent` | [TIdSocketHandleEvent](../types/TIdSocketHandleEvent.md) | `__property TIdSocketHandleEvent OnBeforeBind;` |
| `OnAfterBind: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAfterBind;` |
| `OnBeforeListenerRun: TIdNotifyThreadEvent` | [TIdNotifyThreadEvent](../types/TIdNotifyThreadEvent.md) | `__property TIdNotifyThreadEvent OnBeforeListenerRun;` |
| `OnContextCreated: TIdServerThreadEvent` | [TIdServerThreadEvent](../types/TIdServerThreadEvent.md) | `__property TIdServerThreadEvent OnContextCreated;` |
| `OnConnect: TIdServerThreadEvent` | [TIdServerThreadEvent](../types/TIdServerThreadEvent.md) | `__property TIdServerThreadEvent OnConnect;` |
| `OnDisconnect: TIdServerThreadEvent` | [TIdServerThreadEvent](../types/TIdServerThreadEvent.md) | `__property TIdServerThreadEvent OnDisconnect;` |
| `OnException: TIdServerThreadExceptionEvent` | [TIdServerThreadExceptionEvent](../types/TIdServerThreadExceptionEvent.md) | `__property TIdServerThreadExceptionEvent OnException;` |
| `OnListenException: TIdListenExceptionEvent` | [TIdListenExceptionEvent](../types/TIdListenExceptionEvent.md) | `__property TIdListenExceptionEvent OnListenException;` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
procedure StartListening;
procedure StopListening;
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall StartListening();
void __fastcall StopListening();
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

