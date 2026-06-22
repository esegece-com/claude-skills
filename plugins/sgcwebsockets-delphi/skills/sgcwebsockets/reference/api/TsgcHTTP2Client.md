# TsgcHTTP2Client

unit: sgcHTTP
Edition: requires SGC_HTTP2

Add `sgcHTTP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `Host: String` | `String` | `__property UnicodeString Host;` |
| `Port: Integer` | `Integer` | `__property int Port;` |
| `ConnectTimeout: Integer` | `Integer` | `__property int ConnectTimeout;` |
| `ReadTimeout: Integer` | `Integer` | `__property int ReadTimeout;` |
| `TLS: Boolean` | `Boolean` | `__property bool TLS;` |
| `Proxy: TsgcTCPProxy_Options` | [TsgcTCPProxy_Options](../types/TsgcTCPProxy_Options.md) | `__property TsgcTCPProxy_Options * Proxy;` |
| `IPVersion: TIdIPVersion` | `TIdIPVersion` | `__property TIdIPVersion * IPVersion;` |
| `NotifyEvents: TwsNotifyEvent` | [TwsNotifyEvent](../types/TwsNotifyEvent.md) | `__property TwsNotifyEvent NotifyEvents;` |
| `LogFile: TsgcTCPLogFile` | [TsgcTCPLogFile](../types/TsgcTCPLogFile.md) | `__property TsgcTCPLogFile * LogFile;` |
| `HeartBeat: TsgcAI_MCP_Client_HeartBeatOptions` | [TsgcAI_MCP_Client_HeartBeatOptions](../types/TsgcAI_MCP_Client_HeartBeatOptions.md) | `__property TsgcAI_MCP_Client_HeartBeatOptions * HeartBeat;` |
| `WatchDog: TsgcTCPWatchDog_Options` | [TsgcTCPWatchDog_Options](../types/TsgcTCPWatchDog_Options.md) | `__property TsgcTCPWatchDog_Options * WatchDog;` |
| `Throttle: TsgcTCPThrottle` | [TsgcTCPThrottle](../types/TsgcTCPThrottle.md) | `__property TsgcTCPThrottle * Throttle;` |
| `TLSOptions: TsgcTCPTLS_Options` | [TsgcTCPTLS_Options](../types/TsgcTCPTLS_Options.md) | `__property TsgcTCPTLS_Options * TLSOptions;` |
| `Request: TsgcHTTP2Request` | [TsgcHTTP2Request](../types/TsgcHTTP2Request.md) | `__property TsgcHTTP2Request * Request;` |
| `Settings: TsgcHTTP2Settings` | [TsgcHTTP2Settings](../types/TsgcHTTP2Settings.md) | `__property TsgcHTTP2Settings * Settings;` |
| `Authentication: TsgcHTTP2_Authentication_Options` | [TsgcHTTP2_Authentication_Options](../types/TsgcHTTP2_Authentication_Options.md) | `__property TsgcHTTP2_Authentication_Options * Authentication;` |
| `HTTP2Options: TsgcWSHTTP2Client_Options` | [TsgcWSHTTP2Client_Options](../types/TsgcWSHTTP2Client_Options.md) | `__property TsgcWSHTTP2Client_Options * HTTP2Options;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `HTTP2Connection: TsgcHTTP2ConnectionClient (read-only)` | [TsgcHTTP2ConnectionClient](../types/TsgcHTTP2ConnectionClient.md) | `__property TsgcHTTP2ConnectionClient * HTTP2Connection /* read-only */;` |
| `RequestMaxRetries: Integer` | `Integer` | `__property int RequestMaxRetries;` |
| `Response: TsgcHTTP2Response (read-only)` | [TsgcHTTP2Response](../types/TsgcHTTP2Response.md) | `__property TsgcHTTP2Response * Response /* read-only */;` |
| `TCPKeepAlive: TsgcTCPKeepAlive` | [TsgcTCPKeepAlive](../types/TsgcTCPKeepAlive.md) | `__property TsgcTCPKeepAlive * TCPKeepAlive;` |
| `Connection: TsgcTCPConnection (read-only)` | [TsgcTCPConnection](../types/TsgcTCPConnection.md) | `__property TsgcTCPConnection * Connection /* read-only */;` |
| `UseNagle: Boolean` | `Boolean` | `__property bool UseNagle;` |
| `WriteTimeout: Integer` | `Integer` | `__property int WriteTimeout;` |
| `TCPMode: TsgcTCPMode` | `TsgcTCPMode` | `__property TsgcTCPMode * TCPMode;` |
| `BoundPortMax: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMax;` |
| `BoundPortMin: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMin;` |
| `LingerState: Integer` | `Integer` | `__property int LingerState;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnHTTP2Connect: TsgcHTTP2ClientConnectEvent` | [TsgcHTTP2ClientConnectEvent](../types/TsgcHTTP2ClientConnectEvent.md) | `__property TsgcHTTP2ClientConnectEvent OnHTTP2Connect;` |
| `OnHTTP2GoAway: TsgcHTTP2ClientGoAwayEvent` | [TsgcHTTP2ClientGoAwayEvent](../types/TsgcHTTP2ClientGoAwayEvent.md) | `__property TsgcHTTP2ClientGoAwayEvent OnHTTP2GoAway;` |
| `OnHTTP2RSTStream: TsgcHTTP2ClientRSTStreamEvent` | [TsgcHTTP2ClientRSTStreamEvent](../types/TsgcHTTP2ClientRSTStreamEvent.md) | `__property TsgcHTTP2ClientRSTStreamEvent OnHTTP2RSTStream;` |
| `OnHTTP2Response: TsgcHTTP2ClientResponseEvent` | [TsgcHTTP2ClientResponseEvent](../types/TsgcHTTP2ClientResponseEvent.md) | `__property TsgcHTTP2ClientResponseEvent OnHTTP2Response;` |
| `OnHTTP2ResponseFragment: TsgcHTTP2ClientResponseFragmentEvent` | [TsgcHTTP2ClientResponseFragmentEvent](../types/TsgcHTTP2ClientResponseFragmentEvent.md) | `__property TsgcHTTP2ClientResponseFragmentEvent OnHTTP2ResponseFragment;` |
| `OnHTTP2PushPromise: TsgcHTTP2ClientPushPromiseEvent` | [TsgcHTTP2ClientPushPromiseEvent](../types/TsgcHTTP2ClientPushPromiseEvent.md) | `__property TsgcHTTP2ClientPushPromiseEvent OnHTTP2PushPromise;` |
| `OnHTTP2Disconnect: TsgcHTTP2ClientDisconnectEvent` | [TsgcHTTP2ClientDisconnectEvent](../types/TsgcHTTP2ClientDisconnectEvent.md) | `__property TsgcHTTP2ClientDisconnectEvent OnHTTP2Disconnect;` |
| `OnHTTP2Exception: TsgcHTTP2ClientExceptionEvent` | [TsgcHTTP2ClientExceptionEvent](../types/TsgcHTTP2ClientExceptionEvent.md) | `__property TsgcHTTP2ClientExceptionEvent OnHTTP2Exception;` |
| `OnHTTP2PendingRequests: TsgcHTTP2ClientPendingRequestsEvent` | [TsgcHTTP2ClientPendingRequestsEvent](../types/TsgcHTTP2ClientPendingRequestsEvent.md) | `__property TsgcHTTP2ClientPendingRequestsEvent OnHTTP2PendingRequests;` |
| `OnHTTP2Authorization: TsgcHTTP2ClientAuthorizationEvent` | [TsgcHTTP2ClientAuthorizationEvent](../types/TsgcHTTP2ClientAuthorizationEvent.md) | `__property TsgcHTTP2ClientAuthorizationEvent OnHTTP2Authorization;` |
| `OnHTTP2BeforeRequest: TsgcHTTPClientBeforeRequestEvent` | [TsgcHTTPClientBeforeRequestEvent](../types/TsgcHTTPClientBeforeRequestEvent.md) | `__property TsgcHTTPClientBeforeRequestEvent OnHTTP2BeforeRequest;` |
| `OnSSLGetHandler: TsgcTCPOnSSLGetHandler` | `TsgcTCPOnSSLGetHandler` | `__property TsgcTCPOnSSLGetHandler * OnSSLGetHandler;` |
| `OnSSLAfterCreateHandler: TsgcTCPOnSSLAfterCreateHandler` | `TsgcTCPOnSSLAfterCreateHandler` | `__property TsgcTCPOnSSLAfterCreateHandler * OnSSLAfterCreateHandler;` |
| `OnSSLVerifyPeer: TsgcOnSSLVerifyPeer` | [TsgcOnSSLVerifyPeer](../types/TsgcOnSSLVerifyPeer.md) | `__property TsgcOnSSLVerifyPeer * OnSSLVerifyPeer;` |
| `OnSChannelVerifyPeer: TsgcSChannelOnVerifyPeerEvent` | [TsgcSChannelOnVerifyPeerEvent](../types/TsgcSChannelOnVerifyPeerEvent.md) | `__property TsgcSChannelOnVerifyPeerEvent OnSChannelVerifyPeer;` |
| `OnAndroidTLSVerifyPeer: TsgcAndroidTLSOnVerifyPeerEvent` | [TsgcAndroidTLSOnVerifyPeerEvent](../types/TsgcAndroidTLSOnVerifyPeerEvent.md) | `__property TsgcAndroidTLSOnVerifyPeerEvent OnAndroidTLSVerifyPeer;` |
| `OnAppleTLSVerifyPeer: TsgcAppleTLSOnVerifyPeerEvent` | [TsgcAppleTLSOnVerifyPeerEvent](../types/TsgcAppleTLSOnVerifyPeerEvent.md) | `__property TsgcAppleTLSOnVerifyPeerEvent OnAppleTLSVerifyPeer;` |

## Methods

Delphi

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

C++Builder

```cpp
void __fastcall ConnectAsync(const UnicodeString aURL);
UnicodeString __fastcall Connect(const UnicodeString aURL);
void __fastcall DeleteAsync(const UnicodeString aURL);
UnicodeString __fastcall Delete(const UnicodeString aURL);
void __fastcall OptionsAsync(const UnicodeString aURL);
UnicodeString __fastcall Options(const UnicodeString aURL);
void __fastcall GetAsync(const UnicodeString aURL);
UnicodeString __fastcall Get(const UnicodeString aURL);
void __fastcall PostAsync(const UnicodeString aURL, const TStream * aSource);
UnicodeString __fastcall Post(const UnicodeString aURL, const TStream * aSource);
void __fastcall PutAsync(const UnicodeString aURL, const TStream * aSource);
UnicodeString __fastcall Put(const UnicodeString aURL, const TStream * aSource);
void __fastcall PatchAsync(const UnicodeString aURL, const TStream * aSource);
UnicodeString __fastcall Patch(const UnicodeString aURL, const TStream * aSource);
void __fastcall TraceAsync(const UnicodeString aURL);
UnicodeString __fastcall Trace(const UnicodeString aURL);
void __fastcall Head(const UnicodeString aURL);
void __fastcall Ping();
void __fastcall Close(Th2ErrorCodes * aCode = h2erNO_ERROR, const UnicodeString aDescription = '');
void __fastcall Disconnect();
void __fastcall AddCommand(const TsgcTCPCommands * aCommand);
void __fastcall AddBytes(const TIdBytes * ABytes);
void __fastcall QueueClear();
```

