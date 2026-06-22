# TIdWebDAV

unit: IdWebDAV

Add `IdWebDAV` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `MaxAuthRetries: Integer` | `Integer` | `__property int MaxAuthRetries;` |
| `AllowCookies: Boolean` | `Boolean` | `__property bool AllowCookies;` |
| `HandleRedirects: Boolean` | `Boolean` | `__property bool HandleRedirects;` |
| `ProtocolVersion: TIdHTTPProtocolVersion` | [TIdHTTPProtocolVersion](../types/TIdHTTPProtocolVersion.md) | `__property TIdHTTPProtocolVersion * ProtocolVersion;` |
| `RedirectMaximum: Integer` | `Integer` | `__property int RedirectMaximum;` |
| `ProxyParams: TIdProxyConnectionInfo` | [TIdProxyConnectionInfo](../types/TIdProxyConnectionInfo.md) | `__property TIdProxyConnectionInfo * ProxyParams;` |
| `Request: TIdHTTPRequest` | [TIdHTTPRequest](../types/TIdHTTPRequest.md) | `__property TIdHTTPRequest * Request;` |
| `HTTPOptions: TIdHTTPOptions` | `TIdHTTPOptions` | `__property TIdHTTPOptions * HTTPOptions;` |
| `CookieManager: TIdCookieManager` | [TIdCookieManager](../types/TIdCookieManager.md) | `__property TIdCookieManager * CookieManager;` |
| `Compressor: TIdZLibCompressorBase` | [TIdZLibCompressorBase](../types/TIdZLibCompressorBase.md) | `__property TIdZLibCompressorBase * Compressor;` |
| `ResponseCode: Integer (read-only)` | `Integer` | `__property int ResponseCode /* read-only */;` |
| `ResponseText: string (read-only)` | `string` | `__property UnicodeString ResponseText /* read-only */;` |
| `Response: TIdHTTPResponse (read-only)` | [TIdHTTPResponse](../types/TIdHTTPResponse.md) | `__property TIdHTTPResponse * Response /* read-only */;` |
| `MetaHTTPEquiv: TIdMetaHTTPEquiv (read-only)` | [TIdMetaHTTPEquiv](../types/TIdMetaHTTPEquiv.md) | `__property TIdMetaHTTPEquiv * MetaHTTPEquiv /* read-only */;` |
| `URL: TIdURI (read-only)` | [TIdURI](../types/TIdURI.md) | `__property TIdURI * URL /* read-only */;` |
| `AuthRetries: Integer (read-only)` | `Integer` | `__property int AuthRetries /* read-only */;` |
| `AuthProxyRetries: Integer (read-only)` | `Integer` | `__property int AuthProxyRetries /* read-only */;` |
| `RedirectCount: Integer (read-only)` | `Integer` | `__property int RedirectCount /* read-only */;` |
| `MaxHeaderLines: integer` | `integer` | `__property int MaxHeaderLines;` |
| `AuthenticationManager: TIdAuthenticationManager` | [TIdAuthenticationManager](../types/TIdAuthenticationManager.md) | `__property TIdAuthenticationManager * AuthenticationManager;` |
| `BoundIP: string` | `string` | `__property UnicodeString BoundIP;` |
| `BoundPort: TIdPort` | `TIdPort` | `__property TIdPort * BoundPort;` |
| `BoundPortMax: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMax;` |
| `BoundPortMin: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMin;` |
| `ConnectTimeout: Integer` | `Integer` | `__property int ConnectTimeout;` |
| `ReadTimeout: Integer` | `Integer` | `__property int ReadTimeout;` |
| `ReuseSocket: TIdReuseSocket` | [TIdReuseSocket](../types/TIdReuseSocket.md) | `__property TIdReuseSocket * ReuseSocket;` |
| `UseNagle: Boolean` | `Boolean` | `__property bool UseNagle;` |
| `LingerState: Integer` | `Integer` | `__property int LingerState;` |
| `Greeting: TIdReply` | [TIdReply](../types/TIdReply.md) | `__property TIdReply * Greeting;` |
| `LastCmdResult: TIdReply (read-only)` | [TIdReply](../types/TIdReply.md) | `__property TIdReply * LastCmdResult /* read-only */;` |
| `ManagedIOHandler: Boolean` | `Boolean` | `__property bool ManagedIOHandler;` |
| `Socket: TIdIOHandlerSocket (read-only)` | [TIdIOHandlerSocket](../types/TIdIOHandlerSocket.md) | `__property TIdIOHandlerSocket * Socket /* read-only */;` |
| `Intercept: TIdConnectionIntercept` | [TIdConnectionIntercept](../types/TIdConnectionIntercept.md) | `__property TIdConnectionIntercept * Intercept;` |
| `IOHandler: TIdIOHandler` | [TIdIOHandler](../types/TIdIOHandler.md) | `__property TIdIOHandler * IOHandler;` |
| `WorkTarget: TIdComponent` | [TIdComponent](../types/TIdComponent.md) | `__property TIdComponent * WorkTarget;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnHeadersAvailable: TIdHTTPOnHeadersAvailable` | [TIdHTTPOnHeadersAvailable](../types/TIdHTTPOnHeadersAvailable.md) | `__property TIdHTTPOnHeadersAvailable * OnHeadersAvailable;` |
| `OnRedirect: TIdHTTPOnRedirectEvent` | [TIdHTTPOnRedirectEvent](../types/TIdHTTPOnRedirectEvent.md) | `__property TIdHTTPOnRedirectEvent OnRedirect;` |
| `OnSelectAuthorization: TIdOnSelectAuthorization` | [TIdOnSelectAuthorization](../types/TIdOnSelectAuthorization.md) | `__property TIdOnSelectAuthorization * OnSelectAuthorization;` |
| `OnSelectProxyAuthorization: TIdOnSelectAuthorization` | [TIdOnSelectAuthorization](../types/TIdOnSelectAuthorization.md) | `__property TIdOnSelectAuthorization * OnSelectProxyAuthorization;` |
| `OnAuthorization: TIdOnAuthorization` | [TIdOnAuthorization](../types/TIdOnAuthorization.md) | `__property TIdOnAuthorization * OnAuthorization;` |
| `OnProxyAuthorization: TIdOnAuthorization` | [TIdOnAuthorization](../types/TIdOnAuthorization.md) | `__property TIdOnAuthorization * OnProxyAuthorization;` |
| `OnChunkReceived: TIdOnChunkReceived` | [TIdOnChunkReceived](../types/TIdOnChunkReceived.md) | `__property TIdOnChunkReceived * OnChunkReceived;` |
| `OnBeforeBind: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnBeforeBind;` |
| `OnAfterBind: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAfterBind;` |
| `OnSocketAllocated: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnSocketAllocated;` |
| `OnConnected: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnConnected;` |
| `OnDisconnected: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDisconnected;` |
| `OnWork: TWorkEvent` | [TWorkEvent](../types/TWorkEvent.md) | `__property TWorkEvent OnWork;` |
| `OnWorkBegin: TWorkBeginEvent` | [TWorkBeginEvent](../types/TWorkBeginEvent.md) | `__property TWorkBeginEvent OnWorkBegin;` |
| `OnWorkEnd: TWorkEndEvent` | [TWorkEndEvent](../types/TWorkEndEvent.md) | `__property TWorkEndEvent OnWorkEnd;` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
procedure DAVCheckIn(const AURL, AComment: string);
procedure DAVCheckOut(const AURL: string; const AXMLQuery: TStream; const AComment: string);
procedure DAVCopy(const AURL, DURL: string; const AResponseContent: TStream; const AOverWrite: boolean = True; const ADepth: string = cDepthInfinity);
procedure DAVDelete(const AURL: string; const ALockToken: string);
procedure DAVLabel(const AURL: string; const AXMLQuery: TStream);
procedure DAVLock(const AURL: string; const AXMLQuery, AResponseContent: TStream; const ALockToken, ATags: string; const ATimeOut: string = cTimeoutInfinite; const AMustExist: Boolean = False; const ADepth: string = '0');
procedure DAVMove(const AURL, DURL: string; const AResponseContent: TStream; const AOverWrite: Boolean = True; const ADepth: string = cDepthInfinity);
procedure DAVOrderPatch(const AURL: string; const AXMLQuery: TStream);
procedure DAVPropFind(const AURL: string; const AXMLQuery, AResponseContent: TStream; const ADepth: string = '0'; const ARangeFrom: Integer = -1; const ARangeTo: Integer = -1);
procedure DAVPropPatch(const AURL: string; const AXMLQuery, AResponseContent: TStream; const ADepth: string = '0');
procedure DAVPut(const AURL: string; const ASource: TStream; const ALockToken: String);
procedure DAVReport(const AURL: string; const AXMLQuery, AResponseContent: TStream);
procedure DAVSearch(const AURL: string; const ARangeFrom, ARangeTo: Integer; const AXMLQuery, AResponseContent: TStream; const ADepth: string = '0');
procedure DAVUnCheckOut(const AURL: String);
procedure DAVUnLock(const AURL: string; const ALockToken: string);
procedure DAVVersionControl(const AURL: string);
procedure DAVMakeCollection(const AURL: string);
procedure Delete(AURL: string; AResponseContent: TStream);
procedure Options(AURL: string; AResponseContent: TStream);
procedure Get(AURL: string; AResponseContent: TStream);
procedure Trace(AURL: string; AResponseContent: TStream);
procedure Head(AURL: string);
function Post(AURL: string; const ASourceFile: String ; ADestEncoding: IIdTextEncoding = nil ): string;
function Put(AURL: string; ASource: TStream ; ADestEncoding: IIdTextEncoding = nil ): string;
procedure Patch(AURL: string; ASource, AResponseContent: TStream);
procedure Connect;
function ConnectAndGetAll: string;
procedure CreateIOHandler(ABaseType: TIdIOHandlerClass = nil);
procedure CheckForGracefulDisconnect(ARaiseExceptionIfDisconnected: Boolean = True);
function CheckResponse(const AResponse: Int16; const AAllowedResponses: array of Int16): Int16;
function Connected: Boolean;
procedure Disconnect;
procedure DisconnectNotifyPeer;
procedure GetInternalResponse(AEncoding: IIdTextEncoding = nil);
function GetResponse(const AAllowedResponse: Int16 = -1; AEncoding: IIdTextEncoding = nil): Int16;
procedure RaiseExceptionForLastCmdResult;
function SendCmd(AOut: string; const AResponse: Int16 = -1; AEncoding: IIdTextEncoding = nil): Int16;
procedure WriteHeader(AHeader: TStrings);
procedure WriteRFCStrings(AStrings: TStrings);
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall DAVCheckIn(const UnicodeString AURL, const UnicodeString AComment);
void __fastcall DAVCheckOut(const UnicodeString AURL, const TStream * AXMLQuery, const UnicodeString AComment);
void __fastcall DAVCopy(const UnicodeString AURL, const UnicodeString DURL, const TStream * AResponseContent, const bool AOverWrite = True, const UnicodeString ADepth = cDepthInfinity);
void __fastcall DAVDelete(const UnicodeString AURL, const UnicodeString ALockToken);
void __fastcall DAVLabel(const UnicodeString AURL, const TStream * AXMLQuery);
void __fastcall DAVLock(const UnicodeString AURL, const TStream * AXMLQuery, const TStream * AResponseContent, const UnicodeString ALockToken, const UnicodeString ATags, const UnicodeString ATimeOut = cTimeoutInfinite, const bool AMustExist = False, const UnicodeString ADepth = '0');
void __fastcall DAVMove(const UnicodeString AURL, const UnicodeString DURL, const TStream * AResponseContent, const bool AOverWrite = True, const UnicodeString ADepth = cDepthInfinity);
void __fastcall DAVOrderPatch(const UnicodeString AURL, const TStream * AXMLQuery);
void __fastcall DAVPropFind(const UnicodeString AURL, const TStream * AXMLQuery, const TStream * AResponseContent, const UnicodeString ADepth = '0', const int ARangeFrom = -1, const int ARangeTo = -1);
void __fastcall DAVPropPatch(const UnicodeString AURL, const TStream * AXMLQuery, const TStream * AResponseContent, const UnicodeString ADepth = '0');
void __fastcall DAVPut(const UnicodeString AURL, const TStream * ASource, const UnicodeString ALockToken);
void __fastcall DAVReport(const UnicodeString AURL, const TStream * AXMLQuery, const TStream * AResponseContent);
void __fastcall DAVSearch(const UnicodeString AURL, const int ARangeFrom, const int ARangeTo, const TStream * AXMLQuery, const TStream * AResponseContent, const UnicodeString ADepth = '0');
void __fastcall DAVUnCheckOut(const UnicodeString AURL);
void __fastcall DAVUnLock(const UnicodeString AURL, const UnicodeString ALockToken);
void __fastcall DAVVersionControl(const UnicodeString AURL);
void __fastcall DAVMakeCollection(const UnicodeString AURL);
void __fastcall Delete(UnicodeString AURL, TStream * AResponseContent);
void __fastcall Options(UnicodeString AURL, TStream * AResponseContent);
void __fastcall Get(UnicodeString AURL, TStream * AResponseContent);
void __fastcall Trace(UnicodeString AURL, TStream * AResponseContent);
void __fastcall Head(UnicodeString AURL);
UnicodeString __fastcall Post(UnicodeString AURL, const UnicodeString ASourceFile, IIdTextEncoding ADestEncoding = nil);
UnicodeString __fastcall Put(UnicodeString AURL, TStream * ASource, IIdTextEncoding ADestEncoding = nil);
void __fastcall Patch(UnicodeString AURL, TStream * ASource, TStream * AResponseContent);
void __fastcall Connect();
UnicodeString __fastcall ConnectAndGetAll();
void __fastcall CreateIOHandler(TIdIOHandlerClass * ABaseType = nil);
void __fastcall CheckForGracefulDisconnect(bool ARaiseExceptionIfDisconnected = True);
Int16 __fastcall CheckResponse(const Int16 AResponse, const array of Int16 AAllowedResponses);
bool __fastcall Connected();
void __fastcall Disconnect();
void __fastcall DisconnectNotifyPeer();
void __fastcall GetInternalResponse(IIdTextEncoding AEncoding = nil);
Int16 __fastcall GetResponse(const Int16 AAllowedResponse = -1, IIdTextEncoding AEncoding = nil);
void __fastcall RaiseExceptionForLastCmdResult();
Int16 __fastcall SendCmd(UnicodeString AOut, const Int16 AResponse = -1, IIdTextEncoding AEncoding = nil);
void __fastcall WriteHeader(TStrings * AHeader);
void __fastcall WriteRFCStrings(TStrings * AStrings);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

