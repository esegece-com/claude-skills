# TsgcWebSocketServer_HTTPAPI

unit: sgcWebSocket
Edition: Enterprise

Add `sgcWebSocket` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `Host: string` | `string` | `__property UnicodeString Host;` |
| `Port: Integer` | `Integer` | `__property int Port;` |
| `Authentication: TsgcWSAuthenticationServer_Options` | [TsgcWSAuthenticationServer_Options](../types/TsgcWSAuthenticationServer_Options.md) | `__property TsgcWSAuthenticationServer_Options * Authentication;` |
| `HeartBeat: TsgcWSHeartBeat_Options` | [TsgcWSHeartBeat_Options](../types/TsgcWSHeartBeat_Options.md) | `__property TsgcWSHeartBeat_Options * HeartBeat;` |
| `Extensions: TsgcWSExtensions` | [TsgcWSExtensions](../types/TsgcWSExtensions.md) | `__property TsgcWSExtensions * Extensions;` |
| `Options: TsgcWSOptionsServer` | [TsgcWSOptionsServer](../types/TsgcWSOptionsServer.md) | `__property TsgcWSOptionsServer * Options;` |
| `QueueOptions: TsgcWSQueueServer_Options` | [TsgcWSQueueServer_Options](../types/TsgcWSQueueServer_Options.md) | `__property TsgcWSQueueServer_Options * QueueOptions;` |
| `SecurityOptions: TsgcWSSecurity_Options` | [TsgcWSSecurity_Options](../types/TsgcWSSecurity_Options.md) | `__property TsgcWSSecurity_Options * SecurityOptions;` |
| `Specifications: TsgcWSSpecifications` | [TsgcWSSpecifications](../types/TsgcWSSpecifications.md) | `__property TsgcWSSpecifications * Specifications;` |
| `LogFile: TsgcWSLogFile` | [TsgcWSLogFile](../types/TsgcWSLogFile.md) | `__property TsgcWSLogFile * LogFile;` |
| `SSL: Boolean` | `Boolean` | `__property bool SSL;` |
| `SSLOptions: TsgcWSSSL_Options_HTTPAPI` | [TsgcWSSSL_Options_HTTPAPI](../types/TsgcWSSSL_Options_HTTPAPI.md) | `__property TsgcWSSSL_Options_HTTPAPI * SSLOptions;` |
| `WatchDog: TsgcWSWatchDogServer_Options` | [TsgcWSWatchDogServer_Options](../types/TsgcWSWatchDogServer_Options.md) | `__property TsgcWSWatchDogServer_Options * WatchDog;` |
| `Timeouts: TsgcWSTimeouts_HTTPAPI` | [TsgcWSTimeouts_HTTPAPI](../types/TsgcWSTimeouts_HTTPAPI.md) | `__property TsgcWSTimeouts_HTTPAPI * Timeouts;` |
| `Asynchronous: Boolean` | `Boolean` | `__property bool Asynchronous;` |
| `BindingOptions: TsgcWSBindings_Options_HTTPAPI` | [TsgcWSBindings_Options_HTTPAPI](../types/TsgcWSBindings_Options_HTTPAPI.md) | `__property TsgcWSBindings_Options_HTTPAPI * BindingOptions;` |
| `MaxConnections: Integer` | `Integer` | `__property int MaxConnections;` |
| `MaxBandwidth: Integer` | `Integer` | `__property int MaxBandwidth;` |
| `ThreadPoolSize: Integer` | `Integer` | `__property int ThreadPoolSize;` |
| `ReadBufferSize: Integer` | `Integer` | `__property int ReadBufferSize;` |
| `FineTune: TsgcServerHTTPAPI_FineTune` | [TsgcServerHTTPAPI_FineTune](../types/TsgcServerHTTPAPI_FineTune.md) | `__property TsgcServerHTTPAPI_FineTune * FineTune;` |
| `HTTPUploadFiles: TsgcHTTPUploadFilesServer` | [TsgcHTTPUploadFilesServer](../types/TsgcHTTPUploadFilesServer.md) | `__property TsgcHTTPUploadFilesServer * HTTPUploadFiles;` |
| `Firewall: TsgcWSFirewall` | [TsgcWSFirewall](../types/TsgcWSFirewall.md) | `__property TsgcWSFirewall * Firewall;` |
| `RateLimiter: TsgcWSRateLimiter` | [TsgcWSRateLimiter](../types/TsgcWSRateLimiter.md) | `__property TsgcWSRateLimiter * RateLimiter;` |
| `APIKeyManager: TsgcWSAPIKeyManager` | [TsgcWSAPIKeyManager](../types/TsgcWSAPIKeyManager.md) | `__property TsgcWSAPIKeyManager * APIKeyManager;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `WriteTimeoutInterval: Integer` | `Integer` | `__property int WriteTimeoutInterval;` |
| `Bindings: TsgcWSBindings` | [TsgcWSBindings](../types/TsgcWSBindings.md) | `__property TsgcWSBindings * Bindings;` |
| `Groups: TsgcWSServerGroups` | [TsgcWSServerGroups](../types/TsgcWSServerGroups.md) | `__property TsgcWSServerGroups * Groups;` |
| `ConnectionsByGUID[const[const Guid: String]: TsgcWSConnectionServer_Base (read-only)` | [TsgcWSConnectionServer_Base](../types/TsgcWSConnectionServer_Base.md) | `__property TsgcWSConnectionServer_Base * ConnectionsByGUID[const[const Guid: String] /* read-only */;` |
| `Connections[Index[Index: Integer]: TsgcWSConnectionServer_Base (read-only)` | [TsgcWSConnectionServer_Base](../types/TsgcWSConnectionServer_Base.md) | `__property TsgcWSConnectionServer_Base * Connections[Index[Index: Integer] /* read-only */;` |
| `Count: Integer (read-only)` | `Integer` | `__property int Count /* read-only */;` |
| `MaxMessageSize: Int64` | `Int64` | `__property long long MaxMessageSize;` |
| `FallBack: TsgcWSFallBack_Options` | [TsgcWSFallBack_Options](../types/TsgcWSFallBack_Options.md) | `__property TsgcWSFallBack_Options * FallBack;` |
| `Optimizations: TsgcWSOptimization_Options` | [TsgcWSOptimization_Options](../types/TsgcWSOptimization_Options.md) | `__property TsgcWSOptimization_Options * Optimizations;` |
| `TCPKeepAlive: TsgcTCPKeepAlive` | [TsgcTCPKeepAlive](../types/TsgcTCPKeepAlive.md) | `__property TsgcTCPKeepAlive * TCPKeepAlive;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnStartup: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnStartup;` |
| `OnShutdown: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnShutdown;` |
| `OnBeforeBinding: TsgcWSHTTPAPIBeforeBinding` | [TsgcWSHTTPAPIBeforeBinding](../types/TsgcWSHTTPAPIBeforeBinding.md) | `__property TsgcWSHTTPAPIBeforeBinding * OnBeforeBinding;` |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnHandshake: TsgcWSHandshakeEvent` | [TsgcWSHandshakeEvent](../types/TsgcWSHandshakeEvent.md) | `__property TsgcWSHandshakeEvent OnHandshake;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |
| `OnAuthentication: TsgcWSAuthenticationEvent` | [TsgcWSAuthenticationEvent](../types/TsgcWSAuthenticationEvent.md) | `__property TsgcWSAuthenticationEvent OnAuthentication;` |
| `OnUnknownProtocol: TsgcWSUnknownProtocolEvent` | [TsgcWSUnknownProtocolEvent](../types/TsgcWSUnknownProtocolEvent.md) | `__property TsgcWSUnknownProtocolEvent OnUnknownProtocol;` |
| `OnAsynchronous: TsgcWSHTTPAPIAsynchronousEvent` | [TsgcWSHTTPAPIAsynchronousEvent](../types/TsgcWSHTTPAPIAsynchronousEvent.md) | `__property TsgcWSHTTPAPIAsynchronousEvent OnAsynchronous;` |
| `OnBeforeHeartBeat: TsgcWSOnBeforeHeartBeatEvent` | [TsgcWSOnBeforeHeartBeatEvent](../types/TsgcWSOnBeforeHeartBeatEvent.md) | `__property TsgcWSOnBeforeHeartBeatEvent OnBeforeHeartBeat;` |
| `OnBeforeForwardHTTP: TsgcWSHTTPAPIBeforeForwardHTTP` | [TsgcWSHTTPAPIBeforeForwardHTTP](../types/TsgcWSHTTPAPIBeforeForwardHTTP.md) | `__property TsgcWSHTTPAPIBeforeForwardHTTP * OnBeforeForwardHTTP;` |
| `OnAfterForwardHTTP: TsgcWSHTTPAPIAfterForwardHTTP` | [TsgcWSHTTPAPIAfterForwardHTTP](../types/TsgcWSHTTPAPIAfterForwardHTTP.md) | `__property TsgcWSHTTPAPIAfterForwardHTTP * OnAfterForwardHTTP;` |
| `OnHTTPRequest: TsgcWSHTTPAPIRequestEvent` | [TsgcWSHTTPAPIRequestEvent](../types/TsgcWSHTTPAPIRequestEvent.md) | `__property TsgcWSHTTPAPIRequestEvent OnHTTPRequest;` |
| `OnTCPConnect: TsgcWSHTTPAPITCPConnect` | [TsgcWSHTTPAPITCPConnect](../types/TsgcWSHTTPAPITCPConnect.md) | `__property TsgcWSHTTPAPITCPConnect * OnTCPConnect;` |
| `OnHTTPUploadBeforeSaveFile: TsgcWSHTTPUploadBeforeSaveFileEvent` | [TsgcWSHTTPUploadBeforeSaveFileEvent](../types/TsgcWSHTTPUploadBeforeSaveFileEvent.md) | `__property TsgcWSHTTPUploadBeforeSaveFileEvent OnHTTPUploadBeforeSaveFile;` |
| `OnHTTPUploadAfterSaveFile: TsgcWSHTTPUploadAfterSaveFileEvent` | [TsgcWSHTTPUploadAfterSaveFileEvent](../types/TsgcWSHTTPUploadAfterSaveFileEvent.md) | `__property TsgcWSHTTPUploadAfterSaveFileEvent OnHTTPUploadAfterSaveFile;` |
| `OnHTTPUploadReadInput: TsgcWSHTTPUploadReadInputEvent` | [TsgcWSHTTPUploadReadInputEvent](../types/TsgcWSHTTPUploadReadInputEvent.md) | `__property TsgcWSHTTPUploadReadInputEvent OnHTTPUploadReadInput;` |
| `OnHTTPUploadBeforeCreatePostStream: TsgcWSHTTPBeforeCreatePostStream` | [TsgcWSHTTPBeforeCreatePostStream](../types/TsgcWSHTTPBeforeCreatePostStream.md) | `__property TsgcWSHTTPBeforeCreatePostStream * OnHTTPUploadBeforeCreatePostStream;` |

## Methods

Delphi

```pascal
function ShareList: TList;
procedure UnShareList;
function LockList:;
procedure UnLockList;
procedure DisconnectAll;
procedure OnServerAuthenticationEvent(Connection: TsgcWSConnection; aUser, aPassword: String; var Authenticated: Boolean);
procedure Start;
procedure Stop;
procedure ReStart;
procedure Broadcast(const aMessage: string; const aChannel: string = ''; const aProtocol: string = ''; const Exclude: String = ''; const Include: String = '');
function WriteData(const aGUID, aMessage: string): Boolean;
procedure Ping;
procedure SetNotifyEvents(const Value: TwsNotifyEvent);
procedure RegisterProtocol(aObject: TsgcWSProtocol);
procedure UnRegisterProtocol(aObject: TsgcWSProtocol);
procedure EnterCS;
procedure LeaveCS;
function AssignedCS: Boolean;
procedure QueueClear;
```

C++Builder

```cpp
TList * __fastcall ShareList();
void __fastcall UnShareList();
void __fastcall LockList();
void __fastcall UnLockList();
void __fastcall DisconnectAll();
void __fastcall OnServerAuthenticationEvent(TsgcWSConnection * Connection, UnicodeString aUser, UnicodeString aPassword, bool &Authenticated);
void __fastcall Start();
void __fastcall Stop();
void __fastcall ReStart();
void __fastcall Broadcast(const UnicodeString aMessage, const UnicodeString aChannel = '', const UnicodeString aProtocol = '', const UnicodeString Exclude = '', const UnicodeString Include = '');
bool __fastcall WriteData(const UnicodeString aGUID, const UnicodeString aMessage);
void __fastcall Ping();
void __fastcall SetNotifyEvents(const TwsNotifyEvent Value);
void __fastcall RegisterProtocol(TsgcWSProtocol * aObject);
void __fastcall UnRegisterProtocol(TsgcWSProtocol * aObject);
void __fastcall EnterCS();
void __fastcall LeaveCS();
bool __fastcall AssignedCS();
void __fastcall QueueClear();
```

