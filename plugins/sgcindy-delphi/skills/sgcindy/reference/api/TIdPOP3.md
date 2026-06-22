# TIdPOP3

unit: IdPOP3

Add `IdPOP3` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `HasAPOP: boolean (read-only)` | `boolean` | `__property bool HasAPOP /* read-only */;` |
| `HasCAPA: boolean (read-only)` | `boolean` | `__property bool HasCAPA /* read-only */;` |
| `AuthType: TIdPOP3AuthenticationType` | [TIdPOP3AuthenticationType](../types/TIdPOP3AuthenticationType.md) | `__property TIdPOP3AuthenticationType * AuthType;` |
| `AutoLogin: Boolean` | `Boolean` | `__property bool AutoLogin;` |
| `Host: String` | `String` | `__property UnicodeString Host;` |
| `Username: String` | `String` | `__property UnicodeString Username;` |
| `UseTLS: TIdUseTLS` | [TIdUseTLS](../types/TIdUseTLS.md) | `__property TIdUseTLS * UseTLS;` |
| `Password: String` | `String` | `__property UnicodeString Password;` |
| `Port: TIdPort` | `TIdPort` | `__property TIdPort * Port;` |
| `SASLMechanisms: TIdSASLEntries` | [TIdSASLEntries](../types/TIdSASLEntries.md) | `__property TIdSASLEntries * SASLMechanisms;` |
| `SASLCanAttemptInitialResponse: Boolean` | `Boolean` | `__property bool SASLCanAttemptInitialResponse;` |
| `MsgLineLength: integer` | `integer` | `__property int MsgLineLength;` |
| `MsgLineFold: string` | `string` | `__property UnicodeString MsgLineFold;` |
| `SupportsTLS: boolean (read-only)` | `boolean` | `__property bool SupportsTLS /* read-only */;` |
| `Capabilities: TStrings (read-only)` | `TStrings` | `__property TStrings * Capabilities /* read-only */;` |
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
| `OnTLSHandShakeFailed: TIdOnTLSNegotiationFailure` | [TIdOnTLSNegotiationFailure](../types/TIdOnTLSNegotiationFailure.md) | `__property TIdOnTLSNegotiationFailure * OnTLSHandShakeFailed;` |
| `OnTLSNotAvailable: TIdOnTLSNegotiationFailure` | [TIdOnTLSNegotiationFailure](../types/TIdOnTLSNegotiationFailure.md) | `__property TIdOnTLSNegotiationFailure * OnTLSNotAvailable;` |
| `OnTLSNegCmdFailed: TIdOnTLSNegotiationFailure` | [TIdOnTLSNegotiationFailure](../types/TIdOnTLSNegotiationFailure.md) | `__property TIdOnTLSNegotiationFailure * OnTLSNegCmdFailed;` |
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
function CheckMessages: Integer;
procedure Connect;
procedure Login;
function Delete(const MsgNum: Integer): Boolean;
procedure DisconnectNotifyPeer;
procedure KeepAlive;
function List(const ADest: TStrings; const AMsgNum: Integer = -1): Boolean;
procedure ParseLIST(ALine: String; var VMsgNum: Integer; var VMsgSize: Int64);
procedure ParseUIDL(ALine: String; var VMsgNum: Integer; var VUidl: String);
function Reset: Boolean;
function Retrieve(const MsgNum: Integer; AMsg: TIdMessage): Boolean;
function RetrieveHeader(const MsgNum: Integer; AMsg: TIdMessage): Boolean;
function RetrieveMsgSize(const MsgNum: Integer): Int64;
function RetrieveMailBoxSize: Int64;
function RetrieveRaw(const aMsgNo: Integer; const aDest: TStrings): boolean;
function RetrieveStats(var VMsgCount: Integer; var VMailBoxSize: Int64): Boolean;
function UIDL(const ADest: TStrings; const AMsgNum: Integer = -1): Boolean;
function Top(const AMsgNum: Integer; const ADest: TStrings; const AMaxLines: Integer = 0): boolean;
function CAPA: Boolean;
procedure ProcessMessage(AMsg: TIdMessage; AHeaderOnly: Boolean = False);
procedure SendMsg(AMsg: TIdMessage; AHeadersOnly: Boolean = False);
function ConnectAndGetAll: string;
procedure CreateIOHandler(ABaseType: TIdIOHandlerClass = nil);
procedure CheckForGracefulDisconnect(ARaiseExceptionIfDisconnected: Boolean = True);
function CheckResponse(const AResponse: Int16; const AAllowedResponses: array of Int16): Int16;
function Connected: Boolean;
procedure Disconnect;
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
int __fastcall CheckMessages();
void __fastcall Connect();
void __fastcall Login();
bool __fastcall Delete(const int MsgNum);
void __fastcall DisconnectNotifyPeer();
void __fastcall KeepAlive();
bool __fastcall List(const TStrings * ADest, const int AMsgNum = -1);
void __fastcall ParseLIST(UnicodeString ALine, int &VMsgNum, long long &VMsgSize);
void __fastcall ParseUIDL(UnicodeString ALine, int &VMsgNum, UnicodeString &VUidl);
bool __fastcall Reset();
bool __fastcall Retrieve(const int MsgNum, TIdMessage * AMsg);
bool __fastcall RetrieveHeader(const int MsgNum, TIdMessage * AMsg);
long long __fastcall RetrieveMsgSize(const int MsgNum);
long long __fastcall RetrieveMailBoxSize();
bool __fastcall RetrieveRaw(const int aMsgNo, const TStrings * aDest);
bool __fastcall RetrieveStats(int &VMsgCount, long long &VMailBoxSize);
bool __fastcall UIDL(const TStrings * ADest, const int AMsgNum = -1);
bool __fastcall Top(const int AMsgNum, const TStrings * ADest, const int AMaxLines = 0);
bool __fastcall CAPA();
void __fastcall ProcessMessage(TIdMessage * AMsg, bool AHeaderOnly = False);
void __fastcall SendMsg(TIdMessage * AMsg, bool AHeadersOnly = False);
UnicodeString __fastcall ConnectAndGetAll();
void __fastcall CreateIOHandler(TIdIOHandlerClass * ABaseType = nil);
void __fastcall CheckForGracefulDisconnect(bool ARaiseExceptionIfDisconnected = True);
Int16 __fastcall CheckResponse(const Int16 AResponse, const array of Int16 AAllowedResponses);
bool __fastcall Connected();
void __fastcall Disconnect();
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

