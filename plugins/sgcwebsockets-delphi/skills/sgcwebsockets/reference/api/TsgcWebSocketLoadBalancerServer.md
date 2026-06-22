# TsgcWebSocketLoadBalancerServer

unit: sgcWebSocket
Edition: Professional and higher

Add `sgcWebSocket` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `Port: Integer` | `Integer` | `__property int Port;` |
| `Bindings: TIdSocketHandles` | [TIdSocketHandles](../types/TIdSocketHandles.md) | `__property TIdSocketHandles * Bindings;` |
| `MaxConnections: Integer` | `Integer` | `__property int MaxConnections;` |
| `SSL: Boolean` | `Boolean` | `__property bool SSL;` |
| `SSLOptions: TsgcWSSSL_Options` | `TsgcWSSSL_Options` | `__property TsgcWSSSL_Options * SSLOptions;` |
| `ThreadPool: Boolean` | `Boolean` | `__property bool ThreadPool;` |
| `ThreadPoolOptions: TsgcWSThreadPool_Options` | [TsgcWSThreadPool_Options](../types/TsgcWSThreadPool_Options.md) | `__property TsgcWSThreadPool_Options * ThreadPoolOptions;` |
| `Extensions: TsgcWSExtensions` | [TsgcWSExtensions](../types/TsgcWSExtensions.md) | `__property TsgcWSExtensions * Extensions;` |
| `Options: TsgcWSOptionsServer` | [TsgcWSOptionsServer](../types/TsgcWSOptionsServer.md) | `__property TsgcWSOptionsServer * Options;` |
| `SecurityOptions: TsgcWSSecurity_Options` | [TsgcWSSecurity_Options](../types/TsgcWSSecurity_Options.md) | `__property TsgcWSSecurity_Options * SecurityOptions;` |
| `Specifications: TsgcWSSpecifications` | [TsgcWSSpecifications](../types/TsgcWSSpecifications.md) | `__property TsgcWSSpecifications * Specifications;` |
| `LogFile: TsgcWSLogFile` | [TsgcWSLogFile](../types/TsgcWSLogFile.md) | `__property TsgcWSLogFile * LogFile;` |
| `Throttle: TsgcWSThrottle` | [TsgcWSThrottle](../types/TsgcWSThrottle.md) | `__property TsgcWSThrottle * Throttle;` |
| `FallBack: TsgcWSFallBack_Options` | [TsgcWSFallBack_Options](../types/TsgcWSFallBack_Options.md) | `__property TsgcWSFallBack_Options * FallBack;` |
| `LoadBalancer: TsgcWSLoadBalancer_Options` | [TsgcWSLoadBalancer_Options](../types/TsgcWSLoadBalancer_Options.md) | `__property TsgcWSLoadBalancer_Options * LoadBalancer;` |
| `HTTP2Options: TsgcWSHTTP2Client_Options` | [TsgcWSHTTP2Client_Options](../types/TsgcWSHTTP2Client_Options.md) | `__property TsgcWSHTTP2Client_Options * HTTP2Options;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `ServerList: TsgcThreadListServerList` | [TsgcThreadListServerList](../types/TsgcThreadListServerList.md) | `__property TsgcThreadListServerList * ServerList;` |
| `MessageReadText: TsgcWSLoadBalancerMessage` | [TsgcWSLoadBalancerMessage](../types/TsgcWSLoadBalancerMessage.md) | `__property TsgcWSLoadBalancerMessage * MessageReadText;` |
| `MessageWriteText: TsgcWSLoadBalancerMessage` | [TsgcWSLoadBalancerMessage](../types/TsgcWSLoadBalancerMessage.md) | `__property TsgcWSLoadBalancerMessage * MessageWriteText;` |
| `MessageReadBinary: TsgcWSLoadBalancerBinary` | [TsgcWSLoadBalancerBinary](../types/TsgcWSLoadBalancerBinary.md) | `__property TsgcWSLoadBalancerBinary * MessageReadBinary;` |
| `MessageWriteBinary: TsgcWSLoadBalancerBinary` | [TsgcWSLoadBalancerBinary](../types/TsgcWSLoadBalancerBinary.md) | `__property TsgcWSLoadBalancerBinary * MessageWriteBinary;` |
| `AutoStartSession: Boolean` | `Boolean` | `__property bool AutoStartSession;` |
| `Charset: string` | `string` | `__property UnicodeString Charset;` |
| `DocumentRoot: String` | `String` | `__property UnicodeString DocumentRoot;` |
| `KeepAlive: Boolean` | `Boolean` | `__property bool KeepAlive;` |
| `MaxRequestBodySize: Int64` | `Int64` | `__property long long MaxRequestBodySize;` |
| `ParseParams: Boolean` | `Boolean` | `__property bool ParseParams;` |
| `ReadEmptySource: Integer` | `Integer` | `__property int ReadEmptySource;` |
| `ReadStartSSL: Integer` | `Integer` | `__property int ReadStartSSL;` |
| `SessionList: TIdHTTPCustomSessionList (read-only)` | [TIdHTTPCustomSessionList](../types/TIdHTTPCustomSessionList.md) | `__property TIdHTTPCustomSessionList * SessionList /* read-only */;` |
| `SessionState: Boolean` | `Boolean` | `__property bool SessionState;` |
| `SessionTimeOut: Integer` | `Integer` | `__property int SessionTimeOut;` |
| `StrictRequestParsing: Boolean` | `Boolean` | `__property bool StrictRequestParsing;` |
| `Groups: TsgcWSServerGroups` | [TsgcWSServerGroups](../types/TsgcWSServerGroups.md) | `__property TsgcWSServerGroups * Groups;` |
| `QueueOptions: TsgcWSQueueServer_Options` | [TsgcWSQueueServer_Options](../types/TsgcWSQueueServer_Options.md) | `__property TsgcWSQueueServer_Options * QueueOptions;` |
| `UseNagle: Boolean` | `Boolean` | `__property bool UseNagle;` |
| `MaxReadBufferSize: Int64` | `Int64` | `__property long long MaxReadBufferSize;` |
| `MaxMessageSize: Int64` | `Int64` | `__property long long MaxMessageSize;` |
| `HTTPUploadFiles: TsgcHTTPUploadFilesServer` | [TsgcHTTPUploadFilesServer](../types/TsgcHTTPUploadFilesServer.md) | `__property TsgcHTTPUploadFilesServer * HTTPUploadFiles;` |
| `IOHandlerOptions: TsgcWSIOHandler_Options` | [TsgcWSIOHandler_Options](../types/TsgcWSIOHandler_Options.md) | `__property TsgcWSIOHandler_Options * IOHandlerOptions;` |
| `Authentication: TsgcWSAuthenticationServer_Options` | [TsgcWSAuthenticationServer_Options](../types/TsgcWSAuthenticationServer_Options.md) | `__property TsgcWSAuthenticationServer_Options * Authentication;` |
| `Firewall: TsgcWSFirewall` | [TsgcWSFirewall](../types/TsgcWSFirewall.md) | `__property TsgcWSFirewall * Firewall;` |
| `RateLimiter: TsgcWSRateLimiter` | [TsgcWSRateLimiter](../types/TsgcWSRateLimiter.md) | `__property TsgcWSRateLimiter * RateLimiter;` |
| `APIKeyManager: TsgcWSAPIKeyManager` | [TsgcWSAPIKeyManager](../types/TsgcWSAPIKeyManager.md) | `__property TsgcWSAPIKeyManager * APIKeyManager;` |
| `ClientLoadBalancer: TsgcWSLoadBalancerClient` | [TsgcWSLoadBalancerClient](../types/TsgcWSLoadBalancerClient.md) | `__property TsgcWSLoadBalancerClient * ClientLoadBalancer;` |
| `ConnectionsByGUID[const[const Guid: String]: TsgcWSConnectionServer (read-only)` | [TsgcWSConnectionServer](../types/TsgcWSConnectionServer.md) | `__property TsgcWSConnectionServer * ConnectionsByGUID[const[const Guid: String] /* read-only */;` |
| `Connections[Index[Index: Integer]: TsgcWSConnectionServer (read-only)` | [TsgcWSConnectionServer](../types/TsgcWSConnectionServer.md) | `__property TsgcWSConnectionServer * Connections[Index[Index: Integer] /* read-only */;` |
| `Count: Integer (read-only)` | `Integer` | `__property int Count /* read-only */;` |
| `Optimizations: TsgcWSOptimization_Options` | [TsgcWSOptimization_Options](../types/TsgcWSOptimization_Options.md) | `__property TsgcWSOptimization_Options * Optimizations;` |
| `WatchDog: TsgcWSWatchDogServer_Options` | [TsgcWSWatchDogServer_Options](../types/TsgcWSWatchDogServer_Options.md) | `__property TsgcWSWatchDogServer_Options * WatchDog;` |
| `HeartBeat: TsgcWSHeartBeat_Options` | [TsgcWSHeartBeat_Options](../types/TsgcWSHeartBeat_Options.md) | `__property TsgcWSHeartBeat_Options * HeartBeat;` |
| `TCPKeepAlive: TsgcTCPKeepAlive` | [TsgcTCPKeepAlive](../types/TsgcTCPKeepAlive.md) | `__property TsgcTCPKeepAlive * TCPKeepAlive;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnHandshake: TsgcWSHandshakeEvent` | [TsgcWSHandshakeEvent](../types/TsgcWSHandshakeEvent.md) | `__property TsgcWSHandshakeEvent OnHandshake;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |
| `OnSSLGetHandler: TsgcWSOnSSLGetHandler` | `TsgcWSOnSSLGetHandler` | `__property TsgcWSOnSSLGetHandler OnSSLGetHandler;` |
| `OnSSLAfterCreateHandler: TsgcWSOnSSLAfterCreateHandler` | `TsgcWSOnSSLAfterCreateHandler` | `__property TsgcWSOnSSLAfterCreateHandler OnSSLAfterCreateHandler;` |
| `OnRawMessage: TsgcWSRawMessageEvent` | [TsgcWSRawMessageEvent](../types/TsgcWSRawMessageEvent.md) | `__property TsgcWSRawMessageEvent OnRawMessage;` |
| `OnClientConnect: TsgcWSLBClientConnectionEvent` | [TsgcWSLBClientConnectionEvent](../types/TsgcWSLBClientConnectionEvent.md) | `__property TsgcWSLBClientConnectionEvent OnClientConnect;` |
| `OnClientDisconnect: TsgcWSLBClientConnectionEvent` | [TsgcWSLBClientConnectionEvent](../types/TsgcWSLBClientConnectionEvent.md) | `__property TsgcWSLBClientConnectionEvent OnClientDisconnect;` |
| `OnClientMessage: TsgcWSLBServerMessageEvent` | [TsgcWSLBServerMessageEvent](../types/TsgcWSLBServerMessageEvent.md) | `__property TsgcWSLBServerMessageEvent OnClientMessage;` |
| `OnClientBinary: TsgcWSLBServerBinaryEvent` | [TsgcWSLBServerBinaryEvent](../types/TsgcWSLBServerBinaryEvent.md) | `__property TsgcWSLBServerBinaryEvent OnClientBinary;` |
| `OnClientFragmented: TsgcWSLBServerBinaryEvent` | [TsgcWSLBServerBinaryEvent](../types/TsgcWSLBServerBinaryEvent.md) | `__property TsgcWSLBServerBinaryEvent OnClientFragmented;` |
| `OnServerConnect: TsgcWSLBServerConnectEvent` | [TsgcWSLBServerConnectEvent](../types/TsgcWSLBServerConnectEvent.md) | `__property TsgcWSLBServerConnectEvent OnServerConnect;` |
| `OnServerDisconnect: TsgcWSLBServerDisconnectEvent` | [TsgcWSLBServerDisconnectEvent](../types/TsgcWSLBServerDisconnectEvent.md) | `__property TsgcWSLBServerDisconnectEvent OnServerDisconnect;` |
| `OnServerReady: TsgcWSLBServerReadyEvent` | [TsgcWSLBServerReadyEvent](../types/TsgcWSLBServerReadyEvent.md) | `__property TsgcWSLBServerReadyEvent OnServerReady;` |
| `OnBeforeSendServerBinding: TsgcWSLBBeforeSendServerHostEvent` | [TsgcWSLBBeforeSendServerHostEvent](../types/TsgcWSLBBeforeSendServerHostEvent.md) | `__property TsgcWSLBBeforeSendServerHostEvent OnBeforeSendServerBinding;` |
| `OnLoadBalancerHTTPRequest: TsgcWSLBHTTPRequestEvent` | [TsgcWSLBHTTPRequestEvent](../types/TsgcWSLBHTTPRequestEvent.md) | `__property TsgcWSLBHTTPRequestEvent OnLoadBalancerHTTPRequest;` |
| `OnLoadBalancerHTTPResponse: TsgcWSLBHTTPResponseEvent` | [TsgcWSLBHTTPResponseEvent](../types/TsgcWSLBHTTPResponseEvent.md) | `__property TsgcWSLBHTTPResponseEvent OnLoadBalancerHTTPResponse;` |
| `OnBeforeCommand: TsgcWSOnBeforeCommand` | [TsgcWSOnBeforeCommand](../types/TsgcWSOnBeforeCommand.md) | `__property TsgcWSOnBeforeCommand OnBeforeCommand;` |
| `OnCommandGet: TIdHTTPCommandEvent` | [TIdHTTPCommandEvent](../types/TIdHTTPCommandEvent.md) | `__property TIdHTTPCommandEvent OnCommandGet;` |
| `OnCommandOther: TIdHTTPCommandEvent` | [TIdHTTPCommandEvent](../types/TIdHTTPCommandEvent.md) | `__property TIdHTTPCommandEvent OnCommandOther;` |
| `OnCreateSession: TIdHTTPCreateSession (read-only)` | [TIdHTTPCreateSession](../types/TIdHTTPCreateSession.md) | `__property TIdHTTPCreateSession * OnCreateSession /* read-only */;` |
| `OnInvalidSession: TIdHTTPInvalidSessionEvent` | [TIdHTTPInvalidSessionEvent](../types/TIdHTTPInvalidSessionEvent.md) | `__property TIdHTTPInvalidSessionEvent OnInvalidSession;` |
| `OnSessionEnd: TIdHTTPSessionEndEvent (read-only)` | [TIdHTTPSessionEndEvent](../types/TIdHTTPSessionEndEvent.md) | `__property TIdHTTPSessionEndEvent OnSessionEnd /* read-only */;` |
| `OnSessionStart: TIdHTTPSessionStartEvent (read-only)` | [TIdHTTPSessionStartEvent](../types/TIdHTTPSessionStartEvent.md) | `__property TIdHTTPSessionStartEvent OnSessionStart /* read-only */;` |
| `OnBeforeForwardHTTP: TsgcWSOnBeforeForwardHTTP` | [TsgcWSOnBeforeForwardHTTP](../types/TsgcWSOnBeforeForwardHTTP.md) | `__property TsgcWSOnBeforeForwardHTTP OnBeforeForwardHTTP;` |
| `OnAfterForwardHTTP: TsgcWSOnAfterForwardHTTP` | [TsgcWSOnAfterForwardHTTP](../types/TsgcWSOnAfterForwardHTTP.md) | `__property TsgcWSOnAfterForwardHTTP OnAfterForwardHTTP;` |
| `OnHTTP2BeforeAsyncRequest: TsgcWSOnBeforeHttp2AsyncRequest` | [TsgcWSOnBeforeHttp2AsyncRequest](../types/TsgcWSOnBeforeHttp2AsyncRequest.md) | `__property TsgcWSOnBeforeHttp2AsyncRequest OnHTTP2BeforeAsyncRequest;` |
| `OnTCPConnect: TsgcWSOnTCPConnect` | [TsgcWSOnTCPConnect](../types/TsgcWSOnTCPConnect.md) | `__property TsgcWSOnTCPConnect OnTCPConnect;` |
| `OnSSLVerifyPeer: TsgcOnSSLVerifyPeer` | [TsgcOnSSLVerifyPeer](../types/TsgcOnSSLVerifyPeer.md) | `__property TsgcOnSSLVerifyPeer * OnSSLVerifyPeer;` |
| `OnSSLALPNSelect: TsgcWSOnSSLALPNSelect` | [TsgcWSOnSSLALPNSelect](../types/TsgcWSOnSSLALPNSelect.md) | `__property TsgcWSOnSSLALPNSelect OnSSLALPNSelect;` |
| `OnBeforeHeartBeat: TsgcWSOnBeforeHeartBeatEvent` | [TsgcWSOnBeforeHeartBeatEvent](../types/TsgcWSOnBeforeHeartBeatEvent.md) | `__property TsgcWSOnBeforeHeartBeatEvent OnBeforeHeartBeat;` |
| `OnLoadBalancerConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnLoadBalancerConnect;` |
| `OnLoadBalancerDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnLoadBalancerDisconnect;` |
| `OnLoadBalancerError: TsgcWSLoadBalancerErrorEvent` | [TsgcWSLoadBalancerErrorEvent](../types/TsgcWSLoadBalancerErrorEvent.md) | `__property TsgcWSLoadBalancerErrorEvent OnLoadBalancerError;` |
| `OnStartup: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnStartup;` |
| `OnShutdown: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnShutdown;` |
| `OnAuthentication: TsgcWSAuthenticationEvent` | [TsgcWSAuthenticationEvent](../types/TsgcWSAuthenticationEvent.md) | `__property TsgcWSAuthenticationEvent OnAuthentication;` |
| `OnUnknownAuthentication: TsgcWSUnknownAuthenticationEvent` | [TsgcWSUnknownAuthenticationEvent](../types/TsgcWSUnknownAuthenticationEvent.md) | `__property TsgcWSUnknownAuthenticationEvent OnUnknownAuthentication;` |
| `OnHTTPUploadBeforeSaveFile: TsgcWSHTTPUploadBeforeSaveFileEvent` | [TsgcWSHTTPUploadBeforeSaveFileEvent](../types/TsgcWSHTTPUploadBeforeSaveFileEvent.md) | `__property TsgcWSHTTPUploadBeforeSaveFileEvent OnHTTPUploadBeforeSaveFile;` |
| `OnHTTPUploadAfterSaveFile: TsgcWSHTTPUploadAfterSaveFileEvent` | [TsgcWSHTTPUploadAfterSaveFileEvent](../types/TsgcWSHTTPUploadAfterSaveFileEvent.md) | `__property TsgcWSHTTPUploadAfterSaveFileEvent OnHTTPUploadAfterSaveFile;` |
| `OnHTTPUploadBeforeCreatePostStream: TsgcWSHTTPBeforeCreatePostStream` | [TsgcWSHTTPBeforeCreatePostStream](../types/TsgcWSHTTPBeforeCreatePostStream.md) | `__property TsgcWSHTTPBeforeCreatePostStream * OnHTTPUploadBeforeCreatePostStream;` |
| `OnHTTPUploadReadInput: TsgcWSHTTPUploadReadInputEvent` | [TsgcWSHTTPUploadReadInputEvent](../types/TsgcWSHTTPUploadReadInputEvent.md) | `__property TsgcWSHTTPUploadReadInputEvent OnHTTPUploadReadInput;` |
| `OnUnknownProtocol: TsgcWSUnknownProtocolEvent` | [TsgcWSUnknownProtocolEvent](../types/TsgcWSUnknownProtocolEvent.md) | `__property TsgcWSUnknownProtocolEvent OnUnknownProtocol;` |

## Methods

Delphi

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

C++Builder

```cpp
void __fastcall PushPromiseAddPreLoadLinks(const UnicodeString aPathMatch, const TStrings * aLinks);
void __fastcall PushPromiseRemovePreLoadLinks(const UnicodeString aPathMatch);
TList < * __fastcall LockList();
void __fastcall UnLockList();
void __fastcall OnServerAuthenticationEvent(TsgcWSConnection * Connection, UnicodeString aUser, UnicodeString aPassword, bool &Authenticated);
void __fastcall Start();
void __fastcall Stop();
void __fastcall ReStart();
void __fastcall DisconnectAll();
void __fastcall Broadcast(const UnicodeString aMessage, const UnicodeString aChannel = '', const UnicodeString aProtocol = '', const UnicodeString Exclude = '', const UnicodeString Include = '');
bool __fastcall WriteData(const UnicodeString aGuid, const UnicodeString aMessage);
void __fastcall Ping(const UnicodeString aText = '');
void __fastcall SetNotifyEvents(const TwsNotifyEvent Value);
void __fastcall RegisterProtocol(TsgcWSProtocol * aObject);
void __fastcall UnRegisterProtocol(TsgcWSProtocol * aObject);
void __fastcall EnterCS();
void __fastcall LeaveCS();
bool __fastcall AssignedCS();
void __fastcall QueueClear();
```

