# TsgcHTTP2CLient_Base

kind: class
unit: sgcHTTP2_Client

## Properties

| Delphi | Type |
| --- | --- |
| `HTTP2Connection: TsgcHTTP2ConnectionClient (read-only)` | [TsgcHTTP2ConnectionClient](./TsgcHTTP2ConnectionClient.md) |
| `RequestMaxRetries: Integer` | `Integer` |
| `Authentication: TsgcHTTP2_Authentication_Options` | [TsgcHTTP2_Authentication_Options](./TsgcHTTP2_Authentication_Options.md) |
| `Request: TsgcHTTP2Request` | [TsgcHTTP2Request](./TsgcHTTP2Request.md) |
| `Settings: TsgcHTTP2Settings` | [TsgcHTTP2Settings](./TsgcHTTP2Settings.md) |
| `HTTP2Options: TsgcWSHTTP2Client_Options` | [TsgcWSHTTP2Client_Options](./TsgcWSHTTP2Client_Options.md) |
| `Response: TsgcHTTP2Response (read-only)` | [TsgcHTTP2Response](./TsgcHTTP2Response.md) |
| `TCPKeepAlive: TsgcTCPKeepAlive` | [TsgcTCPKeepAlive](./TsgcTCPKeepAlive.md) |
| `Connection: TsgcTCPConnection (read-only)` | [TsgcTCPConnection](./TsgcTCPConnection.md) |
| `LogFile: TsgcTCPLogFile` | [TsgcTCPLogFile](./TsgcTCPLogFile.md) |
| `Throttle: TsgcTCPThrottle` | [TsgcTCPThrottle](./TsgcTCPThrottle.md) |
| `Proxy: TsgcTCPProxy_Options` | [TsgcTCPProxy_Options](./TsgcTCPProxy_Options.md) |
| `WatchDog: TsgcTCPWatchDog_Options` | [TsgcTCPWatchDog_Options](./TsgcTCPWatchDog_Options.md) |
| `Host: String` | `String` |
| `Port: Integer` | `Integer` |
| `TLS: Boolean` | `Boolean` |
| `TLSOptions: TsgcTCPTLS_Options` | [TsgcTCPTLS_Options](./TsgcTCPTLS_Options.md) |
| `UseNagle: Boolean` | `Boolean` |
| `IPVersion: TIdIPVersion` | `TIdIPVersion` |
| `ConnectTimeout: Integer` | `Integer` |
| `WriteTimeout: Integer` | `Integer` |
| `ReadTimeout: Integer` | `Integer` |
| `TCPMode: TsgcTCPMode` | `TsgcTCPMode` |
| `BoundPortMax: TIdPort` | `TIdPort` |
| `BoundPortMin: TIdPort` | `TIdPort` |
| `LingerState: Integer` | `Integer` |
| `Active: Boolean` | `Boolean` |
| `QueueMessages: Boolean` | `Boolean` |
| `Version: String (read-only)` | `String` |

## Events

| Delphi | Type |
| --- | --- |
| `OnHTTP2Connect: TsgcHTTP2ClientConnectEvent` | [TsgcHTTP2ClientConnectEvent](./TsgcHTTP2ClientConnectEvent.md) |
| `OnHTTP2Response: TsgcHTTP2ClientResponseEvent` | [TsgcHTTP2ClientResponseEvent](./TsgcHTTP2ClientResponseEvent.md) |
| `OnHTTP2ResponseFragment: TsgcHTTP2ClientResponseFragmentEvent` | [TsgcHTTP2ClientResponseFragmentEvent](./TsgcHTTP2ClientResponseFragmentEvent.md) |
| `OnHTTP2GoAway: TsgcHTTP2ClientGoAwayEvent` | [TsgcHTTP2ClientGoAwayEvent](./TsgcHTTP2ClientGoAwayEvent.md) |
| `OnHTTP2PushPromise: TsgcHTTP2ClientPushPromiseEvent` | [TsgcHTTP2ClientPushPromiseEvent](./TsgcHTTP2ClientPushPromiseEvent.md) |
| `OnHTTP2RSTStream: TsgcHTTP2ClientRSTStreamEvent` | [TsgcHTTP2ClientRSTStreamEvent](./TsgcHTTP2ClientRSTStreamEvent.md) |
| `OnHTTP2Disconnect: TsgcHTTP2ClientDisconnectEvent` | [TsgcHTTP2ClientDisconnectEvent](./TsgcHTTP2ClientDisconnectEvent.md) |
| `OnHTTP2Exception: TsgcHTTP2ClientExceptionEvent` | [TsgcHTTP2ClientExceptionEvent](./TsgcHTTP2ClientExceptionEvent.md) |
| `OnHTTP2PendingRequests: TsgcHTTP2ClientPendingRequestsEvent` | [TsgcHTTP2ClientPendingRequestsEvent](./TsgcHTTP2ClientPendingRequestsEvent.md) |
| `OnHTTP2Authorization: TsgcHTTP2ClientAuthorizationEvent` | [TsgcHTTP2ClientAuthorizationEvent](./TsgcHTTP2ClientAuthorizationEvent.md) |
| `OnHTTP2BeforeRequest: TsgcHTTPClientBeforeRequestEvent` | [TsgcHTTPClientBeforeRequestEvent](./TsgcHTTPClientBeforeRequestEvent.md) |
| `OnSSLGetHandler: TsgcTCPOnSSLGetHandler` | `TsgcTCPOnSSLGetHandler` |
| `OnSSLAfterCreateHandler: TsgcTCPOnSSLAfterCreateHandler` | `TsgcTCPOnSSLAfterCreateHandler` |
| `OnSSLVerifyPeer: TsgcOnSSLVerifyPeer` | [TsgcOnSSLVerifyPeer](./TsgcOnSSLVerifyPeer.md) |
| `OnSChannelVerifyPeer: TsgcSChannelOnVerifyPeerEvent` | [TsgcSChannelOnVerifyPeerEvent](./TsgcSChannelOnVerifyPeerEvent.md) |
| `OnAndroidTLSVerifyPeer: TsgcAndroidTLSOnVerifyPeerEvent` | [TsgcAndroidTLSOnVerifyPeerEvent](./TsgcAndroidTLSOnVerifyPeerEvent.md) |
| `OnAppleTLSVerifyPeer: TsgcAppleTLSOnVerifyPeerEvent` | [TsgcAppleTLSOnVerifyPeerEvent](./TsgcAppleTLSOnVerifyPeerEvent.md) |

## Methods

```pascal
procedure ConnectAsync(const aURL: string);
function Connect(const aURL: string): string;
procedure DeleteAsync(const aURL: string);
function Delete(const aURL: string): string;
procedure OptionsAsync(const aURL: string);
function Options(const aURL: string): string;
procedure GetAsync(const aURL: string);
function Get(const aURL: string): string;
procedure PostAsync(const aURL: string; const aSource: TStream);
function Post(const aURL: string; const aSource: TStream): string;
procedure PutAsync(const aURL: string; const aSource: TStream);
function Put(const aURL: string; const aSource: TStream): string;
procedure PatchAsync(const aURL: string; const aSource: TStream);
function Patch(const aURL: string; const aSource: TStream): string;
procedure TraceAsync(const aURL: string);
function Trace(Const aURL: string): string;
procedure Head(const aURL: string);
procedure Ping;
procedure Close(aCode: Th2ErrorCodes = h2erNO_ERROR; const aDescription: String = '');
procedure Disconnect;
procedure AddCommand(const aCommand: TsgcTCPCommands);
procedure AddBytes(const ABytes: TIdBytes);
procedure QueueClear;
```

