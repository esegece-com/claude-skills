# TIdSMTPRelay

unit: IdSMTPRelay

Add `IdSMTPRelay` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `DNSServer: String` | `String` | `__property UnicodeString DNSServer;` |
| `RelaySender: String` | `String` | `__property UnicodeString RelaySender;` |
| `StatusList: TIdSMTPRelayStatusList (read-only)` | [TIdSMTPRelayStatusList](../types/TIdSMTPRelayStatusList.md) | `__property TIdSMTPRelayStatusList * StatusList /* read-only */;` |
| `SSLOptions: TIdSSLSupportOptions` | [TIdSSLSupportOptions](../types/TIdSSLSupportOptions.md) | `__property TIdSSLSupportOptions * SSLOptions;` |
| `MailAgent: string` | `string` | `__property UnicodeString MailAgent;` |
| `HeloName: string` | `string` | `__property UnicodeString HeloName;` |
| `UseEhlo: Boolean` | `Boolean` | `__property bool UseEhlo;` |
| `PipeLine: Boolean` | `Boolean` | `__property bool PipeLine;` |
| `UseVerp: Boolean` | `Boolean` | `__property bool UseVerp;` |
| `VerpDelims: string` | `string` | `__property UnicodeString VerpDelims;` |
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
| `OnDirectSMTPStatus: TIdSMTPRelayStatus` | [TIdSMTPRelayStatus](../types/TIdSMTPRelayStatus.md) | `__property TIdSMTPRelayStatus * OnDirectSMTPStatus;` |
| `OnTLSHandShakeFailed: TIdOnTLSNegotiationFailure` | [TIdOnTLSNegotiationFailure](../types/TIdOnTLSNegotiationFailure.md) | `__property TIdOnTLSNegotiationFailure * OnTLSHandShakeFailed;` |
| `OnTLSNotAvailable: TIdOnTLSNegotiationFailure` | [TIdOnTLSNegotiationFailure](../types/TIdOnTLSNegotiationFailure.md) | `__property TIdOnTLSNegotiationFailure * OnTLSNotAvailable;` |
| `OnTLSNegCmdFailed: TIdOnTLSNegotiationFailure` | [TIdOnTLSNegotiationFailure](../types/TIdOnTLSNegotiationFailure.md) | `__property TIdOnTLSNegotiationFailure * OnTLSNegCmdFailed;` |
| `OnFailedRecipient: TIdSMTPFailedRecipient` | [TIdSMTPFailedRecipient](../types/TIdSMTPFailedRecipient.md) | `__property TIdSMTPFailedRecipient * OnFailedRecipient;` |
| `OnFailedEHLO: TIdSMTPFailedEHLO` | [TIdSMTPFailedEHLO](../types/TIdSMTPFailedEHLO.md) | `__property TIdSMTPFailedEHLO * OnFailedEHLO;` |
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
procedure Assign(Source: TPersistent);
procedure DisconnectNotifyPeer;
procedure Send(AMsg: TIdMessage; ARecipients: TIdEMailAddressList);
procedure ProcessMessage(AMsg: TIdMessage; AHeaderOnly: Boolean = False);
procedure SendMsg(AMsg: TIdMessage; AHeadersOnly: Boolean = False);
procedure Connect;
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
void __fastcall Assign(TPersistent * Source);
void __fastcall DisconnectNotifyPeer();
void __fastcall Send(TIdMessage * AMsg, TIdEMailAddressList * ARecipients);
void __fastcall ProcessMessage(TIdMessage * AMsg, bool AHeaderOnly = False);
void __fastcall SendMsg(TIdMessage * AMsg, bool AHeadersOnly = False);
void __fastcall Connect();
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

