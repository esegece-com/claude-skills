# TsgcWSLoadBalancerClient

kind: class
unit: sgcWebSocket_LoadBalancer_Client

## Properties

| Delphi | Type |
| --- | --- |
| `MessageWriteText: TsgcWSLoadBalancerMessage` | [TsgcWSLoadBalancerMessage](./TsgcWSLoadBalancerMessage.md) |
| `MessageReadText: TsgcWSLoadBalancerMessage` | [TsgcWSLoadBalancerMessage](./TsgcWSLoadBalancerMessage.md) |
| `MessageWriteBinary: TsgcWSLoadBalancerBinary` | [TsgcWSLoadBalancerBinary](./TsgcWSLoadBalancerBinary.md) |
| `MessageReadBinary: TsgcWSLoadBalancerBinary` | [TsgcWSLoadBalancerBinary](./TsgcWSLoadBalancerBinary.md) |
| `Authentication: TsgcWSAuthenticationClient_Options` | [TsgcWSAuthenticationClient_Options](./TsgcWSAuthenticationClient_Options.md) |
| `LoadBalancer: TsgcWSLoadBalancerClient_Options` | [TsgcWSLoadBalancerClient_Options](./TsgcWSLoadBalancerClient_Options.md) |
| `DisableCS: Boolean` | `Boolean` |
| `Connection: TsgcWSConnection (read-only)` | [TsgcWSConnection](./TsgcWSConnection.md) |
| `Proxy: TsgcWSProxy_Options` | [TsgcWSProxy_Options](./TsgcWSProxy_Options.md) |
| `BoundPortMin: TIdPort` | `TIdPort` |
| `BoundPortMax: TIdPort` | `TIdPort` |
| `Protocol: String (read-only)` | `String` |
| `ConnectTimeout: Integer` | `Integer` |
| `Options: TsgcWSOptionsClient` | [TsgcWSOptionsClient](./TsgcWSOptionsClient.md) |
| `ReadTimeout: Integer` | `Integer` |
| `IPVersion: TIdIPVersion` | `TIdIPVersion` |
| `LingerState: Integer` | `Integer` |
| `QueueOptions: TsgcWSQueueClient_Options` | [TsgcWSQueueClient_Options](./TsgcWSQueueClient_Options.md) |
| `UseNagle: Boolean` | `Boolean` |
| `WriteTimeout: Integer` | `Integer` |
| `Throttle: TsgcWSThrottle` | [TsgcWSThrottle](./TsgcWSThrottle.md) |
| `Active: Boolean` | `Boolean` |
| `BoundIP: string` | `string` |
| `BoundPort: TIdPort` | `TIdPort` |
| `Host: String` | `String` |
| `Port: Integer` | `Integer` |
| `TLS: Boolean` | `Boolean` |
| `TLSOptions: TsgcWSTLS_Options` | [TsgcWSTLS_Options](./TsgcWSTLS_Options.md) |
| `FreeConnectionOnDestroy: Boolean` | `Boolean` |
| `WatchDog: TsgcWSWatchDogClient_Options` | [TsgcWSWatchDogClient_Options](./TsgcWSWatchDogClient_Options.md) |
| `URL: String` | `String` |
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
| `OnWriteDataText: TOnWriteDataText` | [TOnWriteDataText](./TOnWriteDataText.md) |
| `OnBroadCastText: TOnBroadCastText` | [TOnBroadCastText](./TOnBroadCastText.md) |
| `OnBroadCastBinary: TOnBroadCastBinary` | [TOnBroadCastBinary](./TOnBroadCastBinary.md) |
| `OnWriteDataBinary: TOnWriteDataBinary` | [TOnWriteDataBinary](./TOnWriteDataBinary.md) |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](./TsgcWSConnectEvent.md) |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](./TsgcWSDisconnectEvent.md) |
| `OnLoadBalancerError: TsgcWSLoadBalancerErrorEvent` | [TsgcWSLoadBalancerErrorEvent](./TsgcWSLoadBalancerErrorEvent.md) |
| `OnBeforeConnect: TsgcWSOnBeforeConnectEvent` | [TsgcWSOnBeforeConnectEvent](./TsgcWSOnBeforeConnectEvent.md) |
| `OnBeforeHeartBeat: TsgcWSOnBeforeHeartBeatEvent` | [TsgcWSOnBeforeHeartBeatEvent](./TsgcWSOnBeforeHeartBeatEvent.md) |
| `OnBeforeWatchDog: TsgcWSOnBeforeWatchDogEvent` | [TsgcWSOnBeforeWatchDogEvent](./TsgcWSOnBeforeWatchDogEvent.md) |
| `OnSSLGetHandler: TsgcWSOnSSLGetHandler` | `TsgcWSOnSSLGetHandler` |
| `OnSSLAfterCreateHandler: TsgcWSOnSSLAfterCreateHandler` | `TsgcWSOnSSLAfterCreateHandler` |
| `OnSSLVerifyPeer: TsgcOnSSLVerifyPeer` | [TsgcOnSSLVerifyPeer](./TsgcOnSSLVerifyPeer.md) |
| `OnSChannelVerifyPeer: TsgcSChannelOnVerifyPeerEvent` | [TsgcSChannelOnVerifyPeerEvent](./TsgcSChannelOnVerifyPeerEvent.md) |
| `OnAndroidTLSVerifyPeer: TsgcAndroidTLSOnVerifyPeerEvent` | [TsgcAndroidTLSOnVerifyPeerEvent](./TsgcAndroidTLSOnVerifyPeerEvent.md) |
| `OnAppleTLSVerifyPeer: TsgcAppleTLSOnVerifyPeerEvent` | [TsgcAppleTLSOnVerifyPeerEvent](./TsgcAppleTLSOnVerifyPeerEvent.md) |
| `OnHandshake: TsgcWSHandshakeEvent` | [TsgcWSHandshakeEvent](./TsgcWSHandshakeEvent.md) |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](./TsgcWSMessageEvent.md) |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](./TsgcWSBinaryEvent.md) |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](./TsgcWSFragmentedEvent.md) |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](./TsgcWSErrorEvent.md) |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](./TsgcExceptionEvent.md) |

## Methods

```pascal
procedure WriteData(const aGuid, aMessage: string);
procedure Broadcast(const aMessage: string; const aChannel: string = ''; const aProtocol: string = ''; const Exclude: String = ''; const Include: String = '');
procedure Ping(const aText: String = '');
procedure ReadRawFileLog(const aFilename: string);
procedure Start;
procedure Stop;
function Connect(const aTimeout: Integer = 10000): Boolean;
function Disconnect(const aTimeout: Integer = 10000): Boolean;
function Connected: Boolean;
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

