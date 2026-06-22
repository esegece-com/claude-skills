# TIdFTPServer

unit: IdFTPServer

Add `IdFTPServer` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `SupportXAUTH: Boolean` | `Boolean` | `__property bool SupportXAUTH;` |
| `Compressor: TIdZLibCompressorBase` | [TIdZLibCompressorBase](../types/TIdZLibCompressorBase.md) | `__property TIdZLibCompressorBase * Compressor;` |
| `CustomSystID: String` | `String` | `__property UnicodeString CustomSystID;` |
| `DirFormat: TIdFTPDirFormat` | [TIdFTPDirFormat](../types/TIdFTPDirFormat.md) | `__property TIdFTPDirFormat * DirFormat;` |
| `PathProcessing: TIdFTPPathProcessing` | [TIdFTPPathProcessing](../types/TIdFTPPathProcessing.md) | `__property TIdFTPPathProcessing * PathProcessing;` |
| `CaseSensitive: Boolean` | `Boolean` | `__property bool CaseSensitive;` |
| `DirSeparator: Char` | `Char` | `__property wchar_t DirSeparator;` |
| `UseTLS: TIdUseTLS` | [TIdUseTLS](../types/TIdUseTLS.md) | `__property TIdUseTLS * UseTLS;` |
| `DefaultPort: TIdPort` | `TIdPort` | `__property TIdPort * DefaultPort;` |
| `AllowAnonymousLogin: Boolean` | `Boolean` | `__property bool AllowAnonymousLogin;` |
| `AnonymousAccounts: TStrings` | `TStrings` | `__property TStrings * AnonymousAccounts;` |
| `AnonymousPassStrictCheck: Boolean` | `Boolean` | `__property bool AnonymousPassStrictCheck;` |
| `DefaultDataPort: TIdPort` | `TIdPort` | `__property TIdPort * DefaultDataPort;` |
| `FTPFileSystem: TIdFTPBaseFileSystem` | [TIdFTPBaseFileSystem](../types/TIdFTPBaseFileSystem.md) | `__property TIdFTPBaseFileSystem * FTPFileSystem;` |
| `FTPSecurityOptions: TIdFTPSecurityOptions` | `TIdFTPSecurityOptions` | `__property TIdFTPSecurityOptions * FTPSecurityOptions;` |
| `EndOfHelpLine: String` | `String` | `__property UnicodeString EndOfHelpLine;` |
| `PASVBoundPortMin: TIdPort` | `TIdPort` | `__property TIdPort * PASVBoundPortMin;` |
| `PASVBoundPortMax: TIdPort` | `TIdPort` | `__property TIdPort * PASVBoundPortMax;` |
| `UserAccounts: TIdCustomUserManager` | [TIdCustomUserManager](../types/TIdCustomUserManager.md) | `__property TIdCustomUserManager * UserAccounts;` |
| `ServerInfo: TIdFTPServerIdentifier` | [TIdFTPServerIdentifier](../types/TIdFTPServerIdentifier.md) | `__property TIdFTPServerIdentifier * ServerInfo;` |
| `SystemType: string` | `string` | `__property UnicodeString SystemType;` |
| `SITECommands: TIdCommandHandlers` | [TIdCommandHandlers](../types/TIdCommandHandlers.md) | `__property TIdCommandHandlers * SITECommands;` |
| `MLSDFacts: TIdMLSDAttrs` | `TIdMLSDAttrs` | `__property TIdMLSDAttrs * MLSDFacts;` |
| `ReplyUnknownSITCommand: TIdReply` | [TIdReply](../types/TIdReply.md) | `__property TIdReply * ReplyUnknownSITCommand;` |
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
| `OnGreeting: TIdOnBanner` | [TIdOnBanner](../types/TIdOnBanner.md) | `__property TIdOnBanner * OnGreeting;` |
| `OnLoginSuccessBanner: TIdOnBanner` | [TIdOnBanner](../types/TIdOnBanner.md) | `__property TIdOnBanner * OnLoginSuccessBanner;` |
| `OnLoginFailureBanner: TIdOnBanner` | [TIdOnBanner](../types/TIdOnBanner.md) | `__property TIdOnBanner * OnLoginFailureBanner;` |
| `OnMD5Cache: TOnCacheChecksum` | [TOnCacheChecksum](../types/TOnCacheChecksum.md) | `__property TOnCacheChecksum OnMD5Cache;` |
| `OnMD5Verify: TOnVerifyChecksum` | [TOnVerifyChecksum](../types/TOnVerifyChecksum.md) | `__property TOnVerifyChecksum OnMD5Verify;` |
| `OnQuitBanner: TIdOnBanner` | [TIdOnBanner](../types/TIdOnBanner.md) | `__property TIdOnBanner * OnQuitBanner;` |
| `OnCustomListDirectory: TOnCustomListDirectoryEvent` | [TOnCustomListDirectoryEvent](../types/TOnCustomListDirectoryEvent.md) | `__property TOnCustomListDirectoryEvent OnCustomListDirectory;` |
| `OnCustomPathProcess: TOnCustomPathProcess` | [TOnCustomPathProcess](../types/TOnCustomPathProcess.md) | `__property TOnCustomPathProcess OnCustomPathProcess;` |
| `OnAfterUserLogin: TOnAfterUserLoginEvent` | [TOnAfterUserLoginEvent](../types/TOnAfterUserLoginEvent.md) | `__property TOnAfterUserLoginEvent OnAfterUserLogin;` |
| `OnChangeDirectory: TOnDirectoryEvent` | [TOnDirectoryEvent](../types/TOnDirectoryEvent.md) | `__property TOnDirectoryEvent OnChangeDirectory;` |
| `OnGetFileSize: TOnGetFileSizeEvent` | [TOnGetFileSizeEvent](../types/TOnGetFileSizeEvent.md) | `__property TOnGetFileSizeEvent OnGetFileSize;` |
| `OnGetFileDate: TOnGetFileDateEvent` | [TOnGetFileDateEvent](../types/TOnGetFileDateEvent.md) | `__property TOnGetFileDateEvent OnGetFileDate;` |
| `OnUserLogin: TOnFTPUserLoginEvent` | [TOnFTPUserLoginEvent](../types/TOnFTPUserLoginEvent.md) | `__property TOnFTPUserLoginEvent OnUserLogin;` |
| `OnUserAccount: TOnFTPUserAccountEvent` | [TOnFTPUserAccountEvent](../types/TOnFTPUserAccountEvent.md) | `__property TOnFTPUserAccountEvent OnUserAccount;` |
| `OnListDirectory: TOnListDirectoryEvent` | [TOnListDirectoryEvent](../types/TOnListDirectoryEvent.md) | `__property TOnListDirectoryEvent OnListDirectory;` |
| `OnDataPortBeforeBind: TOnDataPortBind` | [TOnDataPortBind](../types/TOnDataPortBind.md) | `__property TOnDataPortBind OnDataPortBeforeBind;` |
| `OnDataPortAfterBind: TOnDataPortBind` | [TOnDataPortBind](../types/TOnDataPortBind.md) | `__property TOnDataPortBind OnDataPortAfterBind;` |
| `OnRenameFile: TOnRenameFileEvent` | [TOnRenameFileEvent](../types/TOnRenameFileEvent.md) | `__property TOnRenameFileEvent OnRenameFile;` |
| `OnDeleteFile: TOnFileEvent` | [TOnFileEvent](../types/TOnFileEvent.md) | `__property TOnFileEvent OnDeleteFile;` |
| `OnRetrieveFile: TOnRetrieveFileEvent` | [TOnRetrieveFileEvent](../types/TOnRetrieveFileEvent.md) | `__property TOnRetrieveFileEvent OnRetrieveFile;` |
| `OnStoreFile: TOnStoreFileEvent` | [TOnStoreFileEvent](../types/TOnStoreFileEvent.md) | `__property TOnStoreFileEvent OnStoreFile;` |
| `OnMakeDirectory: TOnDirectoryEvent` | [TOnDirectoryEvent](../types/TOnDirectoryEvent.md) | `__property TOnDirectoryEvent OnMakeDirectory;` |
| `OnRemoveDirectory: TOnDirectoryEvent` | [TOnDirectoryEvent](../types/TOnDirectoryEvent.md) | `__property TOnDirectoryEvent OnRemoveDirectory;` |
| `OnStat: TIdOnFTPStatEvent` | [TIdOnFTPStatEvent](../types/TIdOnFTPStatEvent.md) | `__property TIdOnFTPStatEvent OnStat;` |
| `OnCombineFiles: TOnCombineFiles` | [TOnCombineFiles](../types/TOnCombineFiles.md) | `__property TOnCombineFiles OnCombineFiles;` |
| `OnCRCFile: TOnCheckSumFile` | [TOnCheckSumFile](../types/TOnCheckSumFile.md) | `__property TOnCheckSumFile OnCRCFile;` |
| `OnSetCreationTime: TOnSetFileDateEvent` | [TOnSetFileDateEvent](../types/TOnSetFileDateEvent.md) | `__property TOnSetFileDateEvent OnSetCreationTime;` |
| `OnSetModifiedTime: TOnSetFileDateEvent` | [TOnSetFileDateEvent](../types/TOnSetFileDateEvent.md) | `__property TOnSetFileDateEvent OnSetModifiedTime;` |
| `OnFileExistCheck: TOnCheckFileEvent` | [TOnCheckFileEvent](../types/TOnCheckFileEvent.md) | `__property TOnCheckFileEvent OnFileExistCheck;` |
| `OnHostCheck: TOnHostCheck` | [TOnHostCheck](../types/TOnHostCheck.md) | `__property TOnHostCheck OnHostCheck;` |
| `OnSetATTRIB: TOnSetATTRIB` | [TOnSetATTRIB](../types/TOnSetATTRIB.md) | `__property TOnSetATTRIB OnSetATTRIB;` |
| `OnSiteUMASK: TOnSiteUMASK` | [TOnSiteUMASK](../types/TOnSiteUMASK.md) | `__property TOnSiteUMASK OnSiteUMASK;` |
| `OnSiteCHMOD: TOnSiteCHMOD` | [TOnSiteCHMOD](../types/TOnSiteCHMOD.md) | `__property TOnSiteCHMOD OnSiteCHMOD;` |
| `OnSiteCHOWN: TOnSiteCHOWN` | [TOnSiteCHOWN](../types/TOnSiteCHOWN.md) | `__property TOnSiteCHOWN OnSiteCHOWN;` |
| `OnSiteCHGRP: TOnSiteCHGRP` | [TOnSiteCHGRP](../types/TOnSiteCHGRP.md) | `__property TOnSiteCHGRP OnSiteCHGRP;` |
| `OnPASVBeforeBind: TIdOnPASVRange` | [TIdOnPASVRange](../types/TIdOnPASVRange.md) | `__property TIdOnPASVRange * OnPASVBeforeBind;` |
| `OnPASVReply: TIdOnPASV` | [TIdOnPASV](../types/TIdOnPASV.md) | `__property TIdOnPASV * OnPASVReply;` |
| `OnMLST: TIdOnMLST` | [TIdOnMLST](../types/TIdOnMLST.md) | `__property TIdOnMLST * OnMLST;` |
| `OnSiteUTIME: TOnSiteUTIME` | [TOnSiteUTIME](../types/TOnSiteUTIME.md) | `__property TOnSiteUTIME OnSiteUTIME;` |
| `OnAvailDiskSpace: TIdOnDirSizeInfo` | [TIdOnDirSizeInfo](../types/TIdOnDirSizeInfo.md) | `__property TIdOnDirSizeInfo * OnAvailDiskSpace;` |
| `OnCompleteDirSize: TIdOnDirSizeInfo` | [TIdOnDirSizeInfo](../types/TIdOnDirSizeInfo.md) | `__property TIdOnDirSizeInfo * OnCompleteDirSize;` |
| `OnClientID: TIdOnClientID` | [TIdOnClientID](../types/TIdOnClientID.md) | `__property TIdOnClientID * OnClientID;` |
| `OnClientIDEx: TIdOnClientIDEx` | [TIdOnClientIDEx](../types/TIdOnClientIDEx.md) | `__property TIdOnClientIDEx * OnClientIDEx;` |
| `OnQuerySSLPort: TIdOnQuerySSLPort` | [TIdOnQuerySSLPort](../types/TIdOnQuerySSLPort.md) | `__property TIdOnQuerySSLPort * OnQuerySSLPort;` |
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

