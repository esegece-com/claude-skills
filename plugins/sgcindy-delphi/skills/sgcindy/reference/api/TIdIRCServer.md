# TIdIRCServer

unit: IdIrcServer

Add `IdIrcServer` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `DefaultPort: TIdPort` | `TIdPort` | `__property TIdPort * DefaultPort;` |
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
| `OnCommandPass: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandPass;` |
| `OnCommandNick: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandNick;` |
| `OnCommandUser: TIdIRCUserEvent` | [TIdIRCUserEvent](../types/TIdIRCUserEvent.md) | `__property TIdIRCUserEvent OnCommandUser;` |
| `OnCommandServer: TIdIRCServerEvent` | [TIdIRCServerEvent](../types/TIdIRCServerEvent.md) | `__property TIdIRCServerEvent OnCommandServer;` |
| `OnCommandOper: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandOper;` |
| `OnCommandQuit: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandQuit;` |
| `OnCommandSQuit: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandSQuit;` |
| `OnCommandJoin: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandJoin;` |
| `OnCommandPart: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandPart;` |
| `OnCommandMode: TIdIRCFiveParmEvent` | [TIdIRCFiveParmEvent](../types/TIdIRCFiveParmEvent.md) | `__property TIdIRCFiveParmEvent OnCommandMode;` |
| `OnCommandTopic: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandTopic;` |
| `OnCommandNames: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandNames;` |
| `OnCommandList: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandList;` |
| `OnCommandInvite: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandInvite;` |
| `OnCommandKick: TIdIRCThreeParmEvent` | [TIdIRCThreeParmEvent](../types/TIdIRCThreeParmEvent.md) | `__property TIdIRCThreeParmEvent OnCommandKick;` |
| `OnCommandVersion: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandVersion;` |
| `OnCommandStats: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandStats;` |
| `OnCommandLinks: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandLinks;` |
| `OnCommandTime: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandTime;` |
| `OnCommandConnect: TIdIRCThreeParmEvent` | [TIdIRCThreeParmEvent](../types/TIdIRCThreeParmEvent.md) | `__property TIdIRCThreeParmEvent OnCommandConnect;` |
| `OnCommandTrace: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandTrace;` |
| `OnCommandAdmin: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandAdmin;` |
| `OnCommandInfo: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandInfo;` |
| `OnCommandPrivMsg: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandPrivMsg;` |
| `OnCommandNotice: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandNotice;` |
| `OnCommandWho: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandWho;` |
| `OnCommandWhoIs: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandWhoIs;` |
| `OnCommandWhoWas: TIdIRCThreeParmEvent` | [TIdIRCThreeParmEvent](../types/TIdIRCThreeParmEvent.md) | `__property TIdIRCThreeParmEvent OnCommandWhoWas;` |
| `OnCommandKill: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandKill;` |
| `OnCommandPing: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandPing;` |
| `OnCommandPong: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandPong;` |
| `OnCommandError: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandError;` |
| `OnCommandAway: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandAway;` |
| `OnCommandRehash: TIdIRCGetEvent` | [TIdIRCGetEvent](../types/TIdIRCGetEvent.md) | `__property TIdIRCGetEvent OnCommandRehash;` |
| `OnCommandRestart: TIdIRCGetEvent` | [TIdIRCGetEvent](../types/TIdIRCGetEvent.md) | `__property TIdIRCGetEvent OnCommandRestart;` |
| `OnCommandSummon: TIdIRCTwoParmEvent` | [TIdIRCTwoParmEvent](../types/TIdIRCTwoParmEvent.md) | `__property TIdIRCTwoParmEvent OnCommandSummon;` |
| `OnCommandUsers: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandUsers;` |
| `OnCommandWallops: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandWallops;` |
| `OnCommandUserHost: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandUserHost;` |
| `OnCommandIsOn: TIdIRCOneParmEvent` | [TIdIRCOneParmEvent](../types/TIdIRCOneParmEvent.md) | `__property TIdIRCOneParmEvent OnCommandIsOn;` |
| `OnCommandOther: TIdIRCOtherEvent` | [TIdIRCOtherEvent](../types/TIdIRCOtherEvent.md) | `__property TIdIRCOtherEvent OnCommandOther;` |
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

