# TsgcWSHTTPServer

kind: class
unit: sgcWebSocket_Server

## Properties

| Delphi | Type |
| --- | --- |
| `AutoStartSession: Boolean` | `Boolean` |
| `Charset: string` | `string` |
| `DocumentRoot: String` | `String` |
| `KeepAlive: Boolean` | `Boolean` |
| `MaxRequestBodySize: Int64` | `Int64` |
| `ParseParams: Boolean` | `Boolean` |
| `ReadEmptySource: Integer` | `Integer` |
| `ReadStartSSL: Integer` | `Integer` |
| `SessionList: TIdHTTPCustomSessionList (read-only)` | [TIdHTTPCustomSessionList](./TIdHTTPCustomSessionList.md) |
| `SessionState: Boolean` | `Boolean` |
| `SessionTimeOut: Integer` | `Integer` |
| `StrictRequestParsing: Boolean` | `Boolean` |
| `Groups: TsgcWSServerGroups` | [TsgcWSServerGroups](./TsgcWSServerGroups.md) |
| `Throttle: TsgcWSThrottle` | [TsgcWSThrottle](./TsgcWSThrottle.md) |
| `Port: Integer` | `Integer` |
| `Bindings: TIdSocketHandles` | [TIdSocketHandles](./TIdSocketHandles.md) |
| `MaxConnections: Integer` | `Integer` |
| `Options: TsgcWSOptionsServer` | [TsgcWSOptionsServer](./TsgcWSOptionsServer.md) |
| `SecurityOptions: TsgcWSSecurity_Options` | [TsgcWSSecurity_Options](./TsgcWSSecurity_Options.md) |
| `QueueOptions: TsgcWSQueueServer_Options` | [TsgcWSQueueServer_Options](./TsgcWSQueueServer_Options.md) |
| `UseNagle: Boolean` | `Boolean` |
| `MaxReadBufferSize: Int64` | `Int64` |
| `MaxMessageSize: Int64` | `Int64` |
| `SSLOptions: TsgcWSSSL_Options` | `TsgcWSSSL_Options` |
| `SSL: Boolean` | `Boolean` |
| `HTTPUploadFiles: TsgcHTTPUploadFilesServer` | [TsgcHTTPUploadFilesServer](./TsgcHTTPUploadFilesServer.md) |
| `ThreadPoolOptions: TsgcWSThreadPool_Options` | [TsgcWSThreadPool_Options](./TsgcWSThreadPool_Options.md) |
| `ThreadPool: Boolean` | `Boolean` |
| `IOHandlerOptions: TsgcWSIOHandler_Options` | [TsgcWSIOHandler_Options](./TsgcWSIOHandler_Options.md) |
| `Authentication: TsgcWSAuthenticationServer_Options` | [TsgcWSAuthenticationServer_Options](./TsgcWSAuthenticationServer_Options.md) |
| `FallBack: TsgcWSFallBack_Options` | [TsgcWSFallBack_Options](./TsgcWSFallBack_Options.md) |
| `Firewall: TsgcWSFirewall` | [TsgcWSFirewall](./TsgcWSFirewall.md) |
| `RateLimiter: TsgcWSRateLimiter` | [TsgcWSRateLimiter](./TsgcWSRateLimiter.md) |
| `APIKeyManager: TsgcWSAPIKeyManager` | [TsgcWSAPIKeyManager](./TsgcWSAPIKeyManager.md) |
| `LoadBalancer: TsgcWSLoadBalancerServer_Options` | [TsgcWSLoadBalancerServer_Options](./TsgcWSLoadBalancerServer_Options.md) |
| `ClientLoadBalancer: TsgcWSLoadBalancerClient` | [TsgcWSLoadBalancerClient](./TsgcWSLoadBalancerClient.md) |
| `ConnectionsByGUID[const[const Guid: String]: TsgcWSConnectionServer (read-only)` | [TsgcWSConnectionServer](./TsgcWSConnectionServer.md) |
| `Connections[Index[Index: Integer]: TsgcWSConnectionServer (read-only)` | [TsgcWSConnectionServer](./TsgcWSConnectionServer.md) |
| `Count: Integer (read-only)` | `Integer` |
| `Active: Boolean` | `Boolean` |
| `Optimizations: TsgcWSOptimization_Options` | [TsgcWSOptimization_Options](./TsgcWSOptimization_Options.md) |
| `WatchDog: TsgcWSWatchDogServer_Options` | [TsgcWSWatchDogServer_Options](./TsgcWSWatchDogServer_Options.md) |
| `Specifications: TsgcWSSpecifications` | [TsgcWSSpecifications](./TsgcWSSpecifications.md) |
| `LogFile: TsgcWSLogFile` | [TsgcWSLogFile](./TsgcWSLogFile.md) |
| `HeartBeat: TsgcWSHeartBeat_Options` | [TsgcWSHeartBeat_Options](./TsgcWSHeartBeat_Options.md) |
| `TCPKeepAlive: TsgcTCPKeepAlive` | [TsgcTCPKeepAlive](./TsgcTCPKeepAlive.md) |
| `Extensions: TsgcWSExtensions` | [TsgcWSExtensions](./TsgcWSExtensions.md) |
| `QueueMessages: Boolean` | `Boolean` |
| `Version: String (read-only)` | `String` |

## Events

| Delphi | Type |
| --- | --- |
| `OnBeforeCommand: TsgcWSOnBeforeCommand` | [TsgcWSOnBeforeCommand](./TsgcWSOnBeforeCommand.md) |
| `OnCommandGet: TIdHTTPCommandEvent` | [TIdHTTPCommandEvent](./TIdHTTPCommandEvent.md) |
| `OnCommandOther: TIdHTTPCommandEvent` | [TIdHTTPCommandEvent](./TIdHTTPCommandEvent.md) |
| `OnCreateSession: TIdHTTPCreateSession (read-only)` | [TIdHTTPCreateSession](./TIdHTTPCreateSession.md) |
| `OnInvalidSession: TIdHTTPInvalidSessionEvent` | [TIdHTTPInvalidSessionEvent](./TIdHTTPInvalidSessionEvent.md) |
| `OnSessionEnd: TIdHTTPSessionEndEvent (read-only)` | [TIdHTTPSessionEndEvent](./TIdHTTPSessionEndEvent.md) |
| `OnSessionStart: TIdHTTPSessionStartEvent (read-only)` | [TIdHTTPSessionStartEvent](./TIdHTTPSessionStartEvent.md) |
| `OnBeforeForwardHTTP: TsgcWSOnBeforeForwardHTTP` | [TsgcWSOnBeforeForwardHTTP](./TsgcWSOnBeforeForwardHTTP.md) |
| `OnAfterForwardHTTP: TsgcWSOnAfterForwardHTTP` | [TsgcWSOnAfterForwardHTTP](./TsgcWSOnAfterForwardHTTP.md) |
| `OnHTTP2BeforeAsyncRequest: TsgcWSOnBeforeHttp2AsyncRequest` | [TsgcWSOnBeforeHttp2AsyncRequest](./TsgcWSOnBeforeHttp2AsyncRequest.md) |
| `OnTCPConnect: TsgcWSOnTCPConnect` | [TsgcWSOnTCPConnect](./TsgcWSOnTCPConnect.md) |
| `OnSSLGetHandler: TsgcWSOnSSLGetHandler` | `TsgcWSOnSSLGetHandler` |
| `OnSSLAfterCreateHandler: TsgcWSOnSSLAfterCreateHandler` | `TsgcWSOnSSLAfterCreateHandler` |
| `OnSSLVerifyPeer: TsgcOnSSLVerifyPeer` | [TsgcOnSSLVerifyPeer](./TsgcOnSSLVerifyPeer.md) |
| `OnSSLALPNSelect: TsgcWSOnSSLALPNSelect` | [TsgcWSOnSSLALPNSelect](./TsgcWSOnSSLALPNSelect.md) |
| `OnBeforeHeartBeat: TsgcWSOnBeforeHeartBeatEvent` | [TsgcWSOnBeforeHeartBeatEvent](./TsgcWSOnBeforeHeartBeatEvent.md) |
| `OnLoadBalancerConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](./TsgcWSConnectEvent.md) |
| `OnLoadBalancerDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](./TsgcWSDisconnectEvent.md) |
| `OnLoadBalancerError: TsgcWSLoadBalancerErrorEvent` | [TsgcWSLoadBalancerErrorEvent](./TsgcWSLoadBalancerErrorEvent.md) |
| `OnStartup: TNotifyEvent` | `TNotifyEvent` |
| `OnShutdown: TNotifyEvent` | `TNotifyEvent` |
| `OnAuthentication: TsgcWSAuthenticationEvent` | [TsgcWSAuthenticationEvent](./TsgcWSAuthenticationEvent.md) |
| `OnUnknownAuthentication: TsgcWSUnknownAuthenticationEvent` | [TsgcWSUnknownAuthenticationEvent](./TsgcWSUnknownAuthenticationEvent.md) |
| `OnHTTPUploadBeforeSaveFile: TsgcWSHTTPUploadBeforeSaveFileEvent` | [TsgcWSHTTPUploadBeforeSaveFileEvent](./TsgcWSHTTPUploadBeforeSaveFileEvent.md) |
| `OnHTTPUploadAfterSaveFile: TsgcWSHTTPUploadAfterSaveFileEvent` | [TsgcWSHTTPUploadAfterSaveFileEvent](./TsgcWSHTTPUploadAfterSaveFileEvent.md) |
| `OnHTTPUploadBeforeCreatePostStream: TsgcWSHTTPBeforeCreatePostStream` | [TsgcWSHTTPBeforeCreatePostStream](./TsgcWSHTTPBeforeCreatePostStream.md) |
| `OnHTTPUploadReadInput: TsgcWSHTTPUploadReadInputEvent` | [TsgcWSHTTPUploadReadInputEvent](./TsgcWSHTTPUploadReadInputEvent.md) |
| `OnUnknownProtocol: TsgcWSUnknownProtocolEvent` | [TsgcWSUnknownProtocolEvent](./TsgcWSUnknownProtocolEvent.md) |
| `OnHandshake: TsgcWSHandshakeEvent` | [TsgcWSHandshakeEvent](./TsgcWSHandshakeEvent.md) |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](./TsgcWSConnectEvent.md) |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](./TsgcWSDisconnectEvent.md) |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](./TsgcWSMessageEvent.md) |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](./TsgcWSBinaryEvent.md) |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](./TsgcWSFragmentedEvent.md) |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](./TsgcWSErrorEvent.md) |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](./TsgcExceptionEvent.md) |

## Methods

```pascal
procedure PushPromiseAddPreLoadLinks(const aPathMatch: String; const aLinks: TStrings);
procedure PushPromiseRemovePreLoadLinks(const aPathMatch: String);
function LockList: TList <;
procedure UnLockList;
procedure OnServerAuthenticationEvent(Connection: TsgcWSConnection; aUser, aPassword: String; var Authenticated: Boolean);
procedure Start;
procedure Stop;
procedure ReStart;
procedure DisconnectAll;
procedure Broadcast(const aMessage: string; const aChannel: string = ''; const aProtocol: string = ''; const Exclude: String = ''; const Include: String = '');
function WriteData(const aGuid, aMessage: string): Boolean;
procedure Ping(const aText: string = '');
procedure SetNotifyEvents(const Value: TwsNotifyEvent);
procedure RegisterProtocol(aObject: TsgcWSProtocol);
procedure UnRegisterProtocol(aObject: TsgcWSProtocol);
procedure EnterCS;
procedure LeaveCS;
function AssignedCS: Boolean;
procedure QueueClear;
```

