# TIdHTTPServer

unit: IdHTTPServer

Add `IdHTTPServer` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `MIMETable: TIdThreadSafeMimeTable (read-only)` | [TIdThreadSafeMimeTable](../types/TIdThreadSafeMimeTable.md) | `__property TIdThreadSafeMimeTable * MIMETable /* read-only */;` |
| `SessionList: TIdHTTPCustomSessionList` | [TIdHTTPCustomSessionList](../types/TIdHTTPCustomSessionList.md) | `__property TIdHTTPCustomSessionList * SessionList;` |
| `AutoStartSession: boolean` | `boolean` | `__property bool AutoStartSession;` |
| `DefaultPort: TIdPort` | `TIdPort` | `__property TIdPort * DefaultPort;` |
| `KeepAlive: Boolean` | `Boolean` | `__property bool KeepAlive;` |
| `MaximumHeaderLineCount: Integer` | `Integer` | `__property int MaximumHeaderLineCount;` |
| `ParseParams: boolean` | `boolean` | `__property bool ParseParams;` |
| `ServerSoftware: string` | `string` | `__property UnicodeString ServerSoftware;` |
| `SessionState: Boolean` | `Boolean` | `__property bool SessionState;` |
| `SessionTimeOut: Integer` | `Integer` | `__property int SessionTimeOut;` |
| `SessionIDCookieName: string` | `string` | `__property UnicodeString SessionIDCookieName;` |
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
| `OnCreatePostStream: TIdHTTPCreatePostStream` | [TIdHTTPCreatePostStream](../types/TIdHTTPCreatePostStream.md) | `__property TIdHTTPCreatePostStream * OnCreatePostStream;` |
| `OnDoneWithPostStream: TIdHTTPDoneWithPostStream` | [TIdHTTPDoneWithPostStream](../types/TIdHTTPDoneWithPostStream.md) | `__property TIdHTTPDoneWithPostStream * OnDoneWithPostStream;` |
| `OnCommandGet: TIdHTTPCommandEvent` | [TIdHTTPCommandEvent](../types/TIdHTTPCommandEvent.md) | `__property TIdHTTPCommandEvent OnCommandGet;` |
| `OnCommandError: TIdHTTPCommandError` | [TIdHTTPCommandError](../types/TIdHTTPCommandError.md) | `__property TIdHTTPCommandError * OnCommandError;` |
| `OnCommandOther: TIdHTTPCommandEvent` | [TIdHTTPCommandEvent](../types/TIdHTTPCommandEvent.md) | `__property TIdHTTPCommandEvent OnCommandOther;` |
| `OnCreateSession: TIdHTTPCreateSession` | [TIdHTTPCreateSession](../types/TIdHTTPCreateSession.md) | `__property TIdHTTPCreateSession * OnCreateSession;` |
| `OnInvalidSession: TIdHTTPInvalidSessionEvent` | [TIdHTTPInvalidSessionEvent](../types/TIdHTTPInvalidSessionEvent.md) | `__property TIdHTTPInvalidSessionEvent OnInvalidSession;` |
| `OnHeadersAvailable: TIdHTTPHeadersAvailableEvent` | [TIdHTTPHeadersAvailableEvent](../types/TIdHTTPHeadersAvailableEvent.md) | `__property TIdHTTPHeadersAvailableEvent OnHeadersAvailable;` |
| `OnHeadersBlocked: TIdHTTPHeadersBlockedEvent` | [TIdHTTPHeadersBlockedEvent](../types/TIdHTTPHeadersBlockedEvent.md) | `__property TIdHTTPHeadersBlockedEvent OnHeadersBlocked;` |
| `OnHeaderExpectations: TIdHTTPHeaderExpectationsEvent` | [TIdHTTPHeaderExpectationsEvent](../types/TIdHTTPHeaderExpectationsEvent.md) | `__property TIdHTTPHeaderExpectationsEvent OnHeaderExpectations;` |
| `OnParseAuthentication: TIdHTTPParseAuthenticationEvent` | [TIdHTTPParseAuthenticationEvent](../types/TIdHTTPParseAuthenticationEvent.md) | `__property TIdHTTPParseAuthenticationEvent OnParseAuthentication;` |
| `OnQuerySSLPort: TIdHTTPQuerySSLPortEvent` | [TIdHTTPQuerySSLPortEvent](../types/TIdHTTPQuerySSLPortEvent.md) | `__property TIdHTTPQuerySSLPortEvent OnQuerySSLPort;` |
| `OnSessionStart: TIdHTTPSessionStartEvent` | [TIdHTTPSessionStartEvent](../types/TIdHTTPSessionStartEvent.md) | `__property TIdHTTPSessionStartEvent OnSessionStart;` |
| `OnSessionEnd: TIdHTTPSessionEndEvent` | [TIdHTTPSessionEndEvent](../types/TIdHTTPSessionEndEvent.md) | `__property TIdHTTPSessionEndEvent OnSessionEnd;` |
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
function CreateSession(AContext:TIdContext; HTTPResponse: TIdHTTPResponseInfo; HTTPRequest: TIdHTTPRequestInfo): TIdHTTPSession;
function EndSession(const SessionName: String; const RemoteIP: String = ''): Boolean;
procedure StartListening;
procedure StopListening;
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
TIdHTTPSession * __fastcall CreateSession(TIdContext * AContext, TIdHTTPResponseInfo * HTTPResponse, TIdHTTPRequestInfo * HTTPRequest);
bool __fastcall EndSession(const UnicodeString SessionName, const UnicodeString RemoteIP = '');
void __fastcall StartListening();
void __fastcall StopListening();
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

