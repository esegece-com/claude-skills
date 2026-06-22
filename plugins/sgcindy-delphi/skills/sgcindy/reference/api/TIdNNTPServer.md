# TIdNNTPServer

unit: IdNNTPServer

Add `IdNNTPServer` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `DistributionPatterns: TStrings` | `TStrings` | `__property TStrings * DistributionPatterns;` |
| `Help: TStrings` | `TStrings` | `__property TStrings * Help;` |
| `ImplicitTLS: Boolean` | `Boolean` | `__property bool ImplicitTLS;` |
| `DefaultPort: TIdPort` | `TIdPort` | `__property TIdPort * DefaultPort;` |
| `UseTLS: TIdUseTLS` | [TIdUseTLS](../types/TIdUseTLS.md) | `__property TIdUseTLS * UseTLS;` |
| `OverviewFormat: TStrings` | `TStrings` | `__property TStrings * OverviewFormat;` |
| `SupportedAuthTypes: TIdNNTPAuthTypes` | `TIdNNTPAuthTypes` | `__property TIdNNTPAuthTypes * SupportedAuthTypes;` |
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
| `OnArticleById: TIdNNTPOnMsgDataById` | [TIdNNTPOnMsgDataById](../types/TIdNNTPOnMsgDataById.md) | `__property TIdNNTPOnMsgDataById * OnArticleById;` |
| `OnArticleByNo: TIdNNTPOnMsgDataByNo` | [TIdNNTPOnMsgDataByNo](../types/TIdNNTPOnMsgDataByNo.md) | `__property TIdNNTPOnMsgDataByNo * OnArticleByNo;` |
| `OnAuth: TIdNNTPOnAuth` | [TIdNNTPOnAuth](../types/TIdNNTPOnAuth.md) | `__property TIdNNTPOnAuth * OnAuth;` |
| `OnAuthRequired: TIdNNTPOnAuthRequired` | [TIdNNTPOnAuthRequired](../types/TIdNNTPOnAuthRequired.md) | `__property TIdNNTPOnAuthRequired * OnAuthRequired;` |
| `OnBodyById: TIdNNTPOnMsgDataById` | [TIdNNTPOnMsgDataById](../types/TIdNNTPOnMsgDataById.md) | `__property TIdNNTPOnMsgDataById * OnBodyById;` |
| `OnBodyByNo: TIdNNTPOnMsgDataByNo` | [TIdNNTPOnMsgDataByNo](../types/TIdNNTPOnMsgDataByNo.md) | `__property TIdNNTPOnMsgDataByNo * OnBodyByNo;` |
| `OnCheckMsgNo: TIdNNTPOnCheckMsgNo` | [TIdNNTPOnCheckMsgNo](../types/TIdNNTPOnCheckMsgNo.md) | `__property TIdNNTPOnCheckMsgNo * OnCheckMsgNo;` |
| `OnCheckMsgID: TidNNTPOnCheckMsgId` | [TidNNTPOnCheckMsgId](../types/TidNNTPOnCheckMsgId.md) | `__property TidNNTPOnCheckMsgId * OnCheckMsgID;` |
| `OnHeadById: TIdNNTPOnMsgDataById` | [TIdNNTPOnMsgDataById](../types/TIdNNTPOnMsgDataById.md) | `__property TIdNNTPOnMsgDataById * OnHeadById;` |
| `OnHeadByNo: TIdNNTPOnMsgDataByNo` | [TIdNNTPOnMsgDataByNo](../types/TIdNNTPOnMsgDataByNo.md) | `__property TIdNNTPOnMsgDataByNo * OnHeadByNo;` |
| `OnIHaveCheck: TIdNNTPOnIHaveCheck` | [TIdNNTPOnIHaveCheck](../types/TIdNNTPOnIHaveCheck.md) | `__property TIdNNTPOnIHaveCheck * OnIHaveCheck;` |
| `OnIHavePost: TIdNNTPOnPost` | [TIdNNTPOnPost](../types/TIdNNTPOnPost.md) | `__property TIdNNTPOnPost * OnIHavePost;` |
| `OnStatMsgId: TIdNNTPOnMsgDataById` | [TIdNNTPOnMsgDataById](../types/TIdNNTPOnMsgDataById.md) | `__property TIdNNTPOnMsgDataById * OnStatMsgId;` |
| `OnStatMsgNo: TIdNNTPOnMsgDataByNo` | [TIdNNTPOnMsgDataByNo](../types/TIdNNTPOnMsgDataByNo.md) | `__property TIdNNTPOnMsgDataByNo * OnStatMsgNo;` |
| `OnNextArticle: TIdNNTPOnMovePointer` | [TIdNNTPOnMovePointer](../types/TIdNNTPOnMovePointer.md) | `__property TIdNNTPOnMovePointer * OnNextArticle;` |
| `OnPrevArticle: TIdNNTPOnMovePointer` | [TIdNNTPOnMovePointer](../types/TIdNNTPOnMovePointer.md) | `__property TIdNNTPOnMovePointer * OnPrevArticle;` |
| `OnCheckListGroup: TIdNNTPOnCheckListGroup` | [TIdNNTPOnCheckListGroup](../types/TIdNNTPOnCheckListGroup.md) | `__property TIdNNTPOnCheckListGroup * OnCheckListGroup;` |
| `OnListActiveGroups: TIdNNTPOnListPattern` | [TIdNNTPOnListPattern](../types/TIdNNTPOnListPattern.md) | `__property TIdNNTPOnListPattern * OnListActiveGroups;` |
| `OnListActiveGroupTimes: TIdNNTPOnListPattern` | [TIdNNTPOnListPattern](../types/TIdNNTPOnListPattern.md) | `__property TIdNNTPOnListPattern * OnListActiveGroupTimes;` |
| `OnListDescriptions: TIdNNTPOnListPattern` | [TIdNNTPOnListPattern](../types/TIdNNTPOnListPattern.md) | `__property TIdNNTPOnListPattern * OnListDescriptions;` |
| `OnListDistributions: TIdServerThreadEvent` | [TIdServerThreadEvent](../types/TIdServerThreadEvent.md) | `__property TIdServerThreadEvent OnListDistributions;` |
| `OnListExtensions: TIdServerThreadEvent` | [TIdServerThreadEvent](../types/TIdServerThreadEvent.md) | `__property TIdServerThreadEvent OnListExtensions;` |
| `OnListGroup: TIdServerThreadEvent` | [TIdServerThreadEvent](../types/TIdServerThreadEvent.md) | `__property TIdServerThreadEvent OnListGroup;` |
| `OnListGroups: TIdServerThreadEvent` | [TIdServerThreadEvent](../types/TIdServerThreadEvent.md) | `__property TIdServerThreadEvent OnListGroups;` |
| `OnListHeaders: TIdServerThreadEvent` | [TIdServerThreadEvent](../types/TIdServerThreadEvent.md) | `__property TIdServerThreadEvent OnListHeaders;` |
| `OnListNewGroups: TIdNNTPOnNewGroupsList` | [TIdNNTPOnNewGroupsList](../types/TIdNNTPOnNewGroupsList.md) | `__property TIdNNTPOnNewGroupsList * OnListNewGroups;` |
| `OnListSubscriptions: TIdServerThreadEvent` | [TIdServerThreadEvent](../types/TIdServerThreadEvent.md) | `__property TIdServerThreadEvent OnListSubscriptions;` |
| `OnNewNews: TIdNNTPOnNewNews` | [TIdNNTPOnNewNews](../types/TIdNNTPOnNewNews.md) | `__property TIdNNTPOnNewNews * OnNewNews;` |
| `OnSelectGroup: TIdNNTPOnSelectGroup` | [TIdNNTPOnSelectGroup](../types/TIdNNTPOnSelectGroup.md) | `__property TIdNNTPOnSelectGroup * OnSelectGroup;` |
| `OnPost: TIdNNTPOnPost` | [TIdNNTPOnPost](../types/TIdNNTPOnPost.md) | `__property TIdNNTPOnPost * OnPost;` |
| `OnXHdr: TIdNNTPOnXHdr` | [TIdNNTPOnXHdr](../types/TIdNNTPOnXHdr.md) | `__property TIdNNTPOnXHdr * OnXHdr;` |
| `OnXOver: TIdNNTPOnXOver` | [TIdNNTPOnXOver](../types/TIdNNTPOnXOver.md) | `__property TIdNNTPOnXOver * OnXOver;` |
| `OnXPat: TIdNNTPOnXPat` | [TIdNNTPOnXPat](../types/TIdNNTPOnXPat.md) | `__property TIdNNTPOnXPat * OnXPat;` |
| `OnXROver: TIdNNTPOnXOver` | [TIdNNTPOnXOver](../types/TIdNNTPOnXOver.md) | `__property TIdNNTPOnXOver * OnXROver;` |
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

