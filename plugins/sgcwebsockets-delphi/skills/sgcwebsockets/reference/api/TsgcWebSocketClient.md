# TsgcWebSocketClient

unit: sgcWebSocket

Add `sgcWebSocket` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `Host: String` | `String` | `__property UnicodeString Host;` |
| `Port: Integer` | `Integer` | `__property int Port;` |
| `URL: String` | `String` | `__property UnicodeString URL;` |
| `ConnectTimeout: Integer` | `Integer` | `__property int ConnectTimeout;` |
| `ReadTimeout: Integer` | `Integer` | `__property int ReadTimeout;` |
| `WriteTimeout: Integer` | `Integer` | `__property int WriteTimeout;` |
| `TLS: Boolean` | `Boolean` | `__property bool TLS;` |
| `Proxy: TsgcWSProxy_Options` | [TsgcWSProxy_Options](../types/TsgcWSProxy_Options.md) | `__property TsgcWSProxy_Options * Proxy;` |
| `HeartBeat: TsgcWSHeartBeat_Options` | [TsgcWSHeartBeat_Options](../types/TsgcWSHeartBeat_Options.md) | `__property TsgcWSHeartBeat_Options * HeartBeat;` |
| `IPVersion: TIdIPVersion` | `TIdIPVersion` | `__property TIdIPVersion * IPVersion;` |
| `Authentication: TsgcWSAuthenticationClient_Options` | [TsgcWSAuthenticationClient_Options](../types/TsgcWSAuthenticationClient_Options.md) | `__property TsgcWSAuthenticationClient_Options * Authentication;` |
| `Extensions: TsgcWSExtensions` | [TsgcWSExtensions](../types/TsgcWSExtensions.md) | `__property TsgcWSExtensions * Extensions;` |
| `Options: TsgcWSOptionsClient` | [TsgcWSOptionsClient](../types/TsgcWSOptionsClient.md) | `__property TsgcWSOptionsClient * Options;` |
| `Specifications: TsgcWSSpecifications` | [TsgcWSSpecifications](../types/TsgcWSSpecifications.md) | `__property TsgcWSSpecifications * Specifications;` |
| `NotifyEvents: TwsNotifyEvent` | [TwsNotifyEvent](../types/TwsNotifyEvent.md) | `__property TwsNotifyEvent NotifyEvents;` |
| `LogFile: TsgcWSLogFile` | [TsgcWSLogFile](../types/TsgcWSLogFile.md) | `__property TsgcWSLogFile * LogFile;` |
| `QueueOptions: TsgcWSQueueClient_Options` | [TsgcWSQueueClient_Options](../types/TsgcWSQueueClient_Options.md) | `__property TsgcWSQueueClient_Options * QueueOptions;` |
| `WatchDog: TsgcWSWatchDogClient_Options` | [TsgcWSWatchDogClient_Options](../types/TsgcWSWatchDogClient_Options.md) | `__property TsgcWSWatchDogClient_Options * WatchDog;` |
| `Throttle: TsgcWSThrottle` | [TsgcWSThrottle](../types/TsgcWSThrottle.md) | `__property TsgcWSThrottle * Throttle;` |
| `LoadBalancer: TsgcWSLoadBalancerClient_Options` | [TsgcWSLoadBalancerClient_Options](../types/TsgcWSLoadBalancerClient_Options.md) | `__property TsgcWSLoadBalancerClient_Options * LoadBalancer;` |
| `TLSOptions: TsgcWSTLS_Options` | [TsgcWSTLS_Options](../types/TsgcWSTLS_Options.md) | `__property TsgcWSTLS_Options * TLSOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `DisableCS: Boolean` | `Boolean` | `__property bool DisableCS;` |
| `Connection: TsgcWSConnection (read-only)` | [TsgcWSConnection](../types/TsgcWSConnection.md) | `__property TsgcWSConnection * Connection /* read-only */;` |
| `BoundPortMin: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMin;` |
| `BoundPortMax: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMax;` |
| `Protocol: String (read-only)` | `String` | `__property UnicodeString Protocol /* read-only */;` |
| `LingerState: Integer` | `Integer` | `__property int LingerState;` |
| `UseNagle: Boolean` | `Boolean` | `__property bool UseNagle;` |
| `BoundIP: string` | `string` | `__property UnicodeString BoundIP;` |
| `BoundPort: TIdPort` | `TIdPort` | `__property TIdPort * BoundPort;` |
| `FreeConnectionOnDestroy: Boolean` | `Boolean` | `__property bool FreeConnectionOnDestroy;` |
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
| `OnSSLVerifyPeer: TsgcOnSSLVerifyPeer` | [TsgcOnSSLVerifyPeer](../types/TsgcOnSSLVerifyPeer.md) | `__property TsgcOnSSLVerifyPeer * OnSSLVerifyPeer;` |
| `OnLoadBalancerError: TsgcWSLoadBalancerErrorEvent` | [TsgcWSLoadBalancerErrorEvent](../types/TsgcWSLoadBalancerErrorEvent.md) | `__property TsgcWSLoadBalancerErrorEvent OnLoadBalancerError;` |
| `OnBeforeHeartBeat: TsgcWSOnBeforeHeartBeatEvent` | [TsgcWSOnBeforeHeartBeatEvent](../types/TsgcWSOnBeforeHeartBeatEvent.md) | `__property TsgcWSOnBeforeHeartBeatEvent OnBeforeHeartBeat;` |
| `OnBeforeWatchDog: TsgcWSOnBeforeWatchDogEvent` | [TsgcWSOnBeforeWatchDogEvent](../types/TsgcWSOnBeforeWatchDogEvent.md) | `__property TsgcWSOnBeforeWatchDogEvent OnBeforeWatchDog;` |
| `OnBeforeConnect: TsgcWSOnBeforeConnectEvent` | [TsgcWSOnBeforeConnectEvent](../types/TsgcWSOnBeforeConnectEvent.md) | `__property TsgcWSOnBeforeConnectEvent OnBeforeConnect;` |
| `OnSChannelVerifyPeer: TsgcSChannelOnVerifyPeerEvent` | [TsgcSChannelOnVerifyPeerEvent](../types/TsgcSChannelOnVerifyPeerEvent.md) | `__property TsgcSChannelOnVerifyPeerEvent OnSChannelVerifyPeer;` |
| `OnAndroidTLSVerifyPeer: TsgcAndroidTLSOnVerifyPeerEvent` | [TsgcAndroidTLSOnVerifyPeerEvent](../types/TsgcAndroidTLSOnVerifyPeerEvent.md) | `__property TsgcAndroidTLSOnVerifyPeerEvent OnAndroidTLSVerifyPeer;` |
| `OnAppleTLSVerifyPeer: TsgcAppleTLSOnVerifyPeerEvent` | [TsgcAppleTLSOnVerifyPeerEvent](../types/TsgcAppleTLSOnVerifyPeerEvent.md) | `__property TsgcAppleTLSOnVerifyPeerEvent OnAppleTLSVerifyPeer;` |

## Methods

Delphi

```pascal
procedure Ping(const aText: String = '');
procedure ReadRawFileLog(const aFilename: string);
procedure Start;
procedure Stop;
function Connect(const aTimeout: Integer = 10000): Boolean;
function Disconnect(const aTimeout: Integer = 10000): Boolean;
function Connected: Boolean;
procedure WriteData(const aText: String; const aSize: Integer = 0; const aStreaming: TwsStreaming = stmNone);
function WriteAndWaitData(const aText: String; const aTimeout: Integer = 10000): string;
procedure RegisterProtocol(aObject: TsgcWSProtocol);
procedure UnRegisterProtocol(aObject: TsgcWSProtocol);
procedure RegisterAPI(aObject: TsgcWSAPI);
procedure UnRegisterAPI(aObject: TsgcWSAPI);
procedure EnterCS;
procedure LeaveCS;
function AssignedCS: Boolean;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Ping(const UnicodeString aText = '');
void __fastcall ReadRawFileLog(const UnicodeString aFilename);
void __fastcall Start();
void __fastcall Stop();
bool __fastcall Connect(const int aTimeout = 10000);
bool __fastcall Disconnect(const int aTimeout = 10000);
bool __fastcall Connected();
void __fastcall WriteData(const UnicodeString aText, const int aSize = 0, const TwsStreaming * aStreaming = stmNone);
UnicodeString __fastcall WriteAndWaitData(const UnicodeString aText, const int aTimeout = 10000);
void __fastcall RegisterProtocol(TsgcWSProtocol * aObject);
void __fastcall UnRegisterProtocol(TsgcWSProtocol * aObject);
void __fastcall RegisterAPI(TsgcWSAPI * aObject);
void __fastcall UnRegisterAPI(TsgcWSAPI * aObject);
void __fastcall EnterCS();
void __fastcall LeaveCS();
bool __fastcall AssignedCS();
void __fastcall QueueClear();
```

