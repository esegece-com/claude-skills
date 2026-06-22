# TIdDNSResolver

unit: IdDNSResolver

Add `IdDNSResolver` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `DNSHeader: TDNSHeader (read-only)` | [TDNSHeader](../types/TDNSHeader.md) | `__property TDNSHeader * DNSHeader /* read-only */;` |
| `QueryResult: TQueryResult (read-only)` | [TQueryResult](../types/TQueryResult.md) | `__property TQueryResult * QueryResult /* read-only */;` |
| `InternalQuery: TIdBytes` | `TIdBytes` | `__property TIdBytes * InternalQuery;` |
| `PlainTextResult: TIdBytes` | `TIdBytes` | `__property TIdBytes * PlainTextResult;` |
| `QueryType: TQueryType` | `TQueryType` | `__property TQueryType * QueryType;` |
| `WaitingTime: integer` | `integer` | `__property int WaitingTime;` |
| `AllowRecursiveQueries: boolean` | `boolean` | `__property bool AllowRecursiveQueries;` |
| `Host: string` | `string` | `__property UnicodeString Host;` |
| `Port: TIdPort` | `TIdPort` | `__property TIdPort * Port;` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](../types/TIdIPVersion.md) | `__property TIdIPVersion * IPVersion;` |
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
| `OnDisconnected: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDisconnected;` |
| `OnWork: TWorkEvent` | [TWorkEvent](../types/TWorkEvent.md) | `__property TWorkEvent OnWork;` |
| `OnWorkBegin: TWorkBeginEvent` | [TWorkBeginEvent](../types/TWorkBeginEvent.md) | `__property TWorkBeginEvent OnWorkBegin;` |
| `OnWorkEnd: TWorkEndEvent` | [TWorkEndEvent](../types/TWorkEndEvent.md) | `__property TWorkEndEvent OnWorkEnd;` |
| `OnStatus: TIdStatusEvent` | [TIdStatusEvent](../types/TIdStatusEvent.md) | `__property TIdStatusEvent OnStatus;` |

## Methods

Delphi

```pascal
procedure ClearInternalQuery;
procedure ParseAnswers(DNSHeader: TDNSHeader; Answer: TIdBytes; ResetResult: Boolean = True);
procedure CreateQuery(ADomain: string; SOARR : TIdRR_SOA; QueryClass:integer = Class_IN);
procedure FillResult(AResult: TIdBytes; checkID : boolean = true; ResetResult : boolean = true);
procedure FillResultWithOutCheckId(AResult: TIdBytes);
procedure Resolve(ADomain: string; SOARR : TIdRR_SOA = nil; QClass: integer = Class_IN);
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
void __fastcall ClearInternalQuery();
void __fastcall ParseAnswers(TDNSHeader * DNSHeader, TIdBytes * Answer, bool ResetResult = True);
void __fastcall CreateQuery(UnicodeString ADomain, TIdRR_SOA * SOARR, int QueryClass = Class_IN);
void __fastcall FillResult(TIdBytes * AResult, bool checkID = true, bool ResetResult = true);
void __fastcall FillResultWithOutCheckId(TIdBytes * AResult);
void __fastcall Resolve(UnicodeString ADomain, TIdRR_SOA * SOARR = nil, int QClass = Class_IN);
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

