# TIdIMAP4Server

unit: IdIMAP4Server

Add `IdIMAP4Server` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `DefaultPort: TIdPort` | `TIdPort` | `__property TIdPort * DefaultPort;` |
| `SaferMode: Boolean` | `Boolean` | `__property bool SaferMode;` |
| `UseDefaultMechanismsForUnassignedCommands: Boolean` | `Boolean` | `__property bool UseDefaultMechanismsForUnassignedCommands;` |
| `RootPath: string` | `string` | `__property UnicodeString RootPath;` |
| `DefaultPassword: string` | `string` | `__property UnicodeString DefaultPassword;` |
| `MailBoxSeparator: Char (read-only)` | `Char` | `__property wchar_t MailBoxSeparator /* read-only */;` |
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
| `OnDefMechDoesImapMailBoxExist: TIdIMAP4DefMech1` | [TIdIMAP4DefMech1](../types/TIdIMAP4DefMech1.md) | `__property TIdIMAP4DefMech1 * OnDefMechDoesImapMailBoxExist;` |
| `OnDefMechCreateMailBox: TIdIMAP4DefMech1` | [TIdIMAP4DefMech1](../types/TIdIMAP4DefMech1.md) | `__property TIdIMAP4DefMech1 * OnDefMechCreateMailBox;` |
| `OnDefMechDeleteMailBox: TIdIMAP4DefMech1` | [TIdIMAP4DefMech1](../types/TIdIMAP4DefMech1.md) | `__property TIdIMAP4DefMech1 * OnDefMechDeleteMailBox;` |
| `OnDefMechIsMailBoxOpen: TIdIMAP4DefMech1` | [TIdIMAP4DefMech1](../types/TIdIMAP4DefMech1.md) | `__property TIdIMAP4DefMech1 * OnDefMechIsMailBoxOpen;` |
| `OnDefMechSetupMailbox: TIdIMAP4DefMech2` | [TIdIMAP4DefMech2](../types/TIdIMAP4DefMech2.md) | `__property TIdIMAP4DefMech2 * OnDefMechSetupMailbox;` |
| `OnDefMechNameAndMailBoxToPath: TIdIMAP4DefMech3` | [TIdIMAP4DefMech3](../types/TIdIMAP4DefMech3.md) | `__property TIdIMAP4DefMech3 * OnDefMechNameAndMailBoxToPath;` |
| `OnDefMechGetNextFreeUID: TIdIMAP4DefMech3` | [TIdIMAP4DefMech3](../types/TIdIMAP4DefMech3.md) | `__property TIdIMAP4DefMech3 * OnDefMechGetNextFreeUID;` |
| `OnDefMechRenameMailBox: TIdIMAP4DefMech4` | [TIdIMAP4DefMech4](../types/TIdIMAP4DefMech4.md) | `__property TIdIMAP4DefMech4 * OnDefMechRenameMailBox;` |
| `OnDefMechListMailBox: TIdIMAP4DefMech5` | [TIdIMAP4DefMech5](../types/TIdIMAP4DefMech5.md) | `__property TIdIMAP4DefMech5 * OnDefMechListMailBox;` |
| `OnDefMechDeleteMessage: TIdIMAP4DefMech6` | [TIdIMAP4DefMech6](../types/TIdIMAP4DefMech6.md) | `__property TIdIMAP4DefMech6 * OnDefMechDeleteMessage;` |
| `OnDefMechCopyMessage: TIdIMAP4DefMech7` | [TIdIMAP4DefMech7](../types/TIdIMAP4DefMech7.md) | `__property TIdIMAP4DefMech7 * OnDefMechCopyMessage;` |
| `OnDefMechGetMessageSize: TIdIMAP4DefMech8` | [TIdIMAP4DefMech8](../types/TIdIMAP4DefMech8.md) | `__property TIdIMAP4DefMech8 * OnDefMechGetMessageSize;` |
| `OnDefMechGetMessageHeader: TIdIMAP4DefMech9` | [TIdIMAP4DefMech9](../types/TIdIMAP4DefMech9.md) | `__property TIdIMAP4DefMech9 * OnDefMechGetMessageHeader;` |
| `OnDefMechGetMessageRaw: TIdIMAP4DefMech10` | [TIdIMAP4DefMech10](../types/TIdIMAP4DefMech10.md) | `__property TIdIMAP4DefMech10 * OnDefMechGetMessageRaw;` |
| `OnDefMechOpenMailBox: TIdIMAP4DefMech11` | [TIdIMAP4DefMech11](../types/TIdIMAP4DefMech11.md) | `__property TIdIMAP4DefMech11 * OnDefMechOpenMailBox;` |
| `OnDefMechReinterpretParamAsMailBox: TIdIMAP4DefMech12` | [TIdIMAP4DefMech12](../types/TIdIMAP4DefMech12.md) | `__property TIdIMAP4DefMech12 * OnDefMechReinterpretParamAsMailBox;` |
| `OnDefMechUpdateNextFreeUID: TIdIMAP4DefMech13` | [TIdIMAP4DefMech13](../types/TIdIMAP4DefMech13.md) | `__property TIdIMAP4DefMech13 * OnDefMechUpdateNextFreeUID;` |
| `OnDefMechGetFileNameToWriteAppendMessage: TIdIMAP4DefMech14` | [TIdIMAP4DefMech14](../types/TIdIMAP4DefMech14.md) | `__property TIdIMAP4DefMech14 * OnDefMechGetFileNameToWriteAppendMessage;` |
| `OnBeforeCmd: TIdIMAP4CommandBeforeEvent` | [TIdIMAP4CommandBeforeEvent](../types/TIdIMAP4CommandBeforeEvent.md) | `__property TIdIMAP4CommandBeforeEvent OnBeforeCmd;` |
| `OnBeforeSend: TIdIMAP4CommandBeforeSendEvent` | [TIdIMAP4CommandBeforeSendEvent](../types/TIdIMAP4CommandBeforeSendEvent.md) | `__property TIdIMAP4CommandBeforeSendEvent OnBeforeSend;` |
| `OnCommandCAPABILITY: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandCAPABILITY;` |
| `OnCommandNOOP: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandNOOP;` |
| `OnCommandLOGOUT: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandLOGOUT;` |
| `OnCommandAUTHENTICATE: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandAUTHENTICATE;` |
| `OnCommandLOGIN: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandLOGIN;` |
| `OnCommandSELECT: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandSELECT;` |
| `OnCommandEXAMINE: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandEXAMINE;` |
| `OnCommandCREATE: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandCREATE;` |
| `OnCommandDELETE: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandDELETE;` |
| `OnCommandRENAME: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandRENAME;` |
| `OnCommandSUBSCRIBE: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandSUBSCRIBE;` |
| `OnCommandUNSUBSCRIBE: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandUNSUBSCRIBE;` |
| `OnCommandLIST: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandLIST;` |
| `OnCommandLSUB: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandLSUB;` |
| `OnCommandSTATUS: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandSTATUS;` |
| `OnCommandAPPEND: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandAPPEND;` |
| `OnCommandCHECK: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandCHECK;` |
| `OnCommandCLOSE: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandCLOSE;` |
| `OnCommandEXPUNGE: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandEXPUNGE;` |
| `OnCommandSEARCH: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandSEARCH;` |
| `OnCommandFETCH: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandFETCH;` |
| `OnCommandSTORE: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandSTORE;` |
| `OnCommandCOPY: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandCOPY;` |
| `OnCommandUID: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandUID;` |
| `OnCommandX: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandX;` |
| `OnCommandError: TIMAP4CommandEvent` | [TIMAP4CommandEvent](../types/TIMAP4CommandEvent.md) | `__property TIMAP4CommandEvent OnCommandError;` |
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

