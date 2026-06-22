# TIdNNTP

unit: IdNNTP

Add `IdNNTP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `ModeResult: TIdModeSetResult` | [TIdModeSetResult](../types/TIdModeSetResult.md) | `__property TIdModeSetResult * ModeResult;` |
| `MsgCount: Int64 (read-only)` | `Int64` | `__property long long MsgCount /* read-only */;` |
| `MsgHigh: Int64 (read-only)` | `Int64` | `__property long long MsgHigh /* read-only */;` |
| `MsgLow: Int64 (read-only)` | `Int64` | `__property long long MsgLow /* read-only */;` |
| `Permission: TIdNNTPPermission (read-only)` | [TIdNNTPPermission](../types/TIdNNTPPermission.md) | `__property TIdNNTPPermission * Permission /* read-only */;` |
| `NewsAgent: string` | `string` | `__property UnicodeString NewsAgent;` |
| `Mode: TIdModeType` | [TIdModeType](../types/TIdModeType.md) | `__property TIdModeType * Mode;` |
| `Password: String` | `String` | `__property UnicodeString Password;` |
| `Username: String` | `String` | `__property UnicodeString Username;` |
| `Port: TIdPort` | `TIdPort` | `__property TIdPort * Port;` |
| `Host: String` | `String` | `__property UnicodeString Host;` |
| `UseTLS: TIdUseTLS` | [TIdUseTLS](../types/TIdUseTLS.md) | `__property TIdUseTLS * UseTLS;` |
| `ForceAuth: boolean` | `boolean` | `__property bool ForceAuth;` |
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
| `OnNewsgroupList: TIdEvenTIdNewsgroupList` | [TIdEvenTIdNewsgroupList](../types/TIdEvenTIdNewsgroupList.md) | `__property TIdEvenTIdNewsgroupList * OnNewsgroupList;` |
| `OnNewGroupsList: TIdEvenTIdNewsGroupList` | [TIdEvenTIdNewsGroupList](../types/TIdEvenTIdNewsGroupList.md) | `__property TIdEvenTIdNewsGroupList * OnNewGroupsList;` |
| `OnNewNewsList: TIdEventNewNewsList` | [TIdEventNewNewsList](../types/TIdEventNewNewsList.md) | `__property TIdEventNewNewsList * OnNewNewsList;` |
| `OnXHDREntry: TIdEventXHDREntry` | [TIdEventXHDREntry](../types/TIdEventXHDREntry.md) | `__property TIdEventXHDREntry * OnXHDREntry;` |
| `OnXOVER: TIdEventXOVER` | [TIdEventXOVER](../types/TIdEventXOVER.md) | `__property TIdEventXOVER * OnXOVER;` |
| `OnTLSNotAvailable: TIdOnTLSNegotiationFailure` | [TIdOnTLSNegotiationFailure](../types/TIdOnTLSNegotiationFailure.md) | `__property TIdOnTLSNegotiationFailure * OnTLSNotAvailable;` |
| `OnTLSHandShakeFailed: TIdOnTLSNegotiationFailure` | [TIdOnTLSNegotiationFailure](../types/TIdOnTLSNegotiationFailure.md) | `__property TIdOnTLSNegotiationFailure * OnTLSHandShakeFailed;` |
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
procedure Check(AMsgIDs: TStrings; AResponses: TStrings);
procedure Connect;
procedure DisconnectNotifyPeer;
function GetArticle(AMsg: TIdMessage): Boolean;
function GetBody(AMsg: TIdMessage): Boolean;
function GetHeader(AMsg: TIdMessage): Boolean;
procedure GetNewsgroupList;
procedure GetNewGroupsList(ADate: TDateTime; AGMT: boolean; ADistributions: string);
procedure GetNewNewsList(ANewsgroups: string; ADate: TDateTime; AGMT: boolean; ADistributions: string);
procedure GetOverviewFMT(AResponse: TStrings);
function IsExtCmdSupported(AExtension : String) : Boolean;
procedure IHAVE(AMsg: TStrings);
function Next: Boolean;
function Previous: Boolean;
procedure ParseXOVER(Aline: String; var AArticleIndex : Int64; var ASubject, AFrom : String; var ADate : TDateTime; var AMsgId, AReferences : String; var AByteCount, ALineCount : Integer; var AExtraData : String);
procedure ParseNewsGroup(ALine : String; out ANewsGroup: string; out AHi, ALo : Int64; out AStatus : String);
procedure ParseXHDRLine(ALine : String; out AMsg : String; out AHeaderData : String);
procedure Post(AMsg: TIdMessage);
function SendCmd(AOut: string; const AResponse: array of Int16; AEncoding: IIdTextEncoding = nil): Int16;
function SelectArticle(AMsgNo: Int64): Boolean;
procedure SelectGroup(AGroup: string);
function TakeThis(AMsgID: string; AMsg: TStream): string;
procedure XHDR(AHeader: string; AParam: string; AResponse: TStrings);
procedure XOVER(AParam: string; AResponse: TStrings);
procedure SendAuth;
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
procedure WriteHeader(AHeader: TStrings);
procedure WriteRFCStrings(AStrings: TStrings);
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Check(TStrings * AMsgIDs, TStrings * AResponses);
void __fastcall Connect();
void __fastcall DisconnectNotifyPeer();
bool __fastcall GetArticle(TIdMessage * AMsg);
bool __fastcall GetBody(TIdMessage * AMsg);
bool __fastcall GetHeader(TIdMessage * AMsg);
void __fastcall GetNewsgroupList();
void __fastcall GetNewGroupsList(System::TDateTime ADate, bool AGMT, UnicodeString ADistributions);
void __fastcall GetNewNewsList(UnicodeString ANewsgroups, System::TDateTime ADate, bool AGMT, UnicodeString ADistributions);
void __fastcall GetOverviewFMT(TStrings * AResponse);
bool __fastcall IsExtCmdSupported(UnicodeString AExtension);
void __fastcall IHAVE(TStrings * AMsg);
bool __fastcall Next();
bool __fastcall Previous();
void __fastcall ParseXOVER(UnicodeString Aline, long long &AArticleIndex, UnicodeString &ASubject, UnicodeString &AFrom, System::TDateTime &ADate, UnicodeString &AMsgId, UnicodeString &AReferences, int &AByteCount, int &ALineCount, UnicodeString &AExtraData);
void __fastcall ParseNewsGroup(UnicodeString ALine, UnicodeString &ANewsGroup, long long &AHi, long long &ALo, UnicodeString &AStatus);
void __fastcall ParseXHDRLine(UnicodeString ALine, UnicodeString &AMsg, UnicodeString &AHeaderData);
void __fastcall Post(TIdMessage * AMsg);
Int16 __fastcall SendCmd(UnicodeString AOut, const array of Int16 AResponse, IIdTextEncoding AEncoding = nil);
bool __fastcall SelectArticle(long long AMsgNo);
void __fastcall SelectGroup(UnicodeString AGroup);
UnicodeString __fastcall TakeThis(UnicodeString AMsgID, TStream * AMsg);
void __fastcall XHDR(UnicodeString AHeader, UnicodeString AParam, TStrings * AResponse);
void __fastcall XOVER(UnicodeString AParam, TStrings * AResponse);
void __fastcall SendAuth();
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
void __fastcall WriteHeader(TStrings * AHeader);
void __fastcall WriteRFCStrings(TStrings * AStrings);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

