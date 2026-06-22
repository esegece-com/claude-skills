# TIdIMAP4

unit: IdIMAP4

Add `IdIMAP4` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `ConnectionState: TIdIMAP4ConnectionState (read-only)` | [TIdIMAP4ConnectionState](../types/TIdIMAP4ConnectionState.md) | `__property TIdIMAP4ConnectionState * ConnectionState /* read-only */;` |
| `MailBox: TIdMailBox` | [TIdMailBox](../types/TIdMailBox.md) | `__property TIdMailBox * MailBox;` |
| `IPVersion: TIdIPVersion` | [TIdIPVersion](../types/TIdIPVersion.md) | `__property TIdIPVersion * IPVersion;` |
| `Password: String` | `String` | `__property UnicodeString Password;` |
| `RetrieveOnSelect: TIdRetrieveOnSelect` | [TIdRetrieveOnSelect](../types/TIdRetrieveOnSelect.md) | `__property TIdRetrieveOnSelect * RetrieveOnSelect;` |
| `Port: TIdPort` | `TIdPort` | `__property TIdPort * Port;` |
| `Username: String` | `String` | `__property UnicodeString Username;` |
| `MailBoxSeparator: Char` | `Char` | `__property wchar_t MailBoxSeparator;` |
| `GreetingBanner: string (read-only)` | `string` | `__property UnicodeString GreetingBanner /* read-only */;` |
| `Host: String` | `String` | `__property UnicodeString Host;` |
| `UseTLS: TIdUseTLS` | [TIdUseTLS](../types/TIdUseTLS.md) | `__property TIdUseTLS * UseTLS;` |
| `SASLMechanisms: TIdSASLEntries` | [TIdSASLEntries](../types/TIdSASLEntries.md) | `__property TIdSASLEntries * SASLMechanisms;` |
| `AuthType: TIdIMAP4AuthenticationType` | [TIdIMAP4AuthenticationType](../types/TIdIMAP4AuthenticationType.md) | `__property TIdIMAP4AuthenticationType * AuthType;` |
| `MilliSecsToWaitToClearBuffer: integer` | `integer` | `__property int MilliSecsToWaitToClearBuffer;` |
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
| `OnAlert: TIdAlertEvent` | [TIdAlertEvent](../types/TIdAlertEvent.md) | `__property TIdAlertEvent OnAlert;` |
| `OnWorkForPart: TWorkEvent` | [TWorkEvent](../types/TWorkEvent.md) | `__property TWorkEvent OnWorkForPart;` |
| `OnWorkBeginForPart: TWorkBeginEvent` | [TWorkBeginEvent](../types/TWorkBeginEvent.md) | `__property TWorkBeginEvent OnWorkBeginForPart;` |
| `OnWorkEndForPart: TWorkEndEvent` | [TWorkEndEvent](../types/TWorkEndEvent.md) | `__property TWorkEndEvent OnWorkEndForPart;` |
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
function Capability: Boolean;
function FindHowServerCreatesFolders: TIdIMAP4FolderTreatment;
procedure DoAlert(const AMsg: String);
function AppendMsg(const AMBName: String; AMsg: TIdMessage; const AFlags: TIdMessageFlagsSet = []; const AInternalDateTimeGMT: TDateTime = 0.0): Boolean;
function AppendMsgNoEncodeFromFile(const AMBName: String; ASourceFile: string; const AFlags: TIdMessageFlagsSet = []; const AInternalDateTimeGMT: TDateTime = 0.0): Boolean;
function AppendMsgNoEncodeFromStream(const AMBName: String; AStream: TStream; const AFlags: TIdMessageFlagsSet = []; const AInternalDateTimeGMT: TDateTime = 0.0): Boolean;
function CheckMailBox: Boolean;
function CheckMsgSeen(const AMsgNum: UInt32): Boolean;
procedure Login;
function Connect(const AAutoLogin: boolean = true): Boolean;
function CloseMailBox: Boolean;
function CreateMailBox(const AMBName: String): Boolean;
function DeleteMailBox(const AMBName: String): Boolean;
function DeleteMsgs(const AMsgNumList: array of UInt32): Boolean;
procedure Disconnect(ANotifyPeer: Boolean);
procedure DisconnectNotifyPeer;
function ExamineMailBox(const AMBName: String; AMB: TIdMailBox): Boolean;
function ExpungeMailBox: Boolean;
procedure KeepAlive;
function ListInferiorMailBoxes(AMailBoxList, AInferiorMailBoxList: TStrings): Boolean;
function ListMailBoxes(AMailBoxList: TStrings): Boolean;
function ListSubscribedMailBoxes (AMailBoxList: TStrings): Boolean;
function RenameMailBox(const AOldMBName, ANewMBName: String): Boolean;
function SearchMailBox(const ASearchInfo: array of TIdIMAP4SearchRec; const ACharSet: string = ''): Boolean;
function SelectMailBox(const AMBName: String): Boolean;
function StatusMailBox(const AMBName: String; AMB: TIdMailBox): Boolean;
function StoreFlags(const AMsgNumList: array of UInt32; const AStoreMethod: TIdIMAP4StoreDataItem; const AFlags: TIdMessageFlagsSet): Boolean;
function StoreValue(const AMsgNumList: array of UInt32; const AStoreMethod: TIdIMAP4StoreDataItem; const AField, AValue: String): Boolean;
function SubscribeMailBox(const AMBName: String): Boolean;
function CopyMsg(const AMsgNum: UInt32; const AMBName: String): Boolean;
function CopyMsgs(const AMsgNumList: array of UInt32; const AMBName: String): Boolean;
function Retrieve(const AMsgNum: UInt32; AMsg: TIdMessage): Boolean;
function RetrieveNoDecodeToFile(const AMsgNum: UInt32; ADestFile: string): Boolean;
function RetrieveNoDecodeToFilePeek(const AMsgNum: UInt32; ADestFile: string): Boolean;
function RetrieveNoDecodeToStream(const AMsgNum: UInt32; AStream: TStream): Boolean;
function RetrieveNoDecodeToStreamPeek(const AMsgNum: UInt32; AStream: TStream): Boolean;
function RetrieveAllEnvelopes(AMsgList: TIdMessageCollection): Boolean;
function RetrieveAllHeaders(AMsgList: TIdMessageCollection): Boolean;
function RetrieveFirstHeaders(AMsgList: TIdMessageCollection; ACount: Integer): Boolean;
function RetrieveAllMsgs(AMsgList: TIdMessageCollection): Boolean;
function RetrieveFirstMsgs(AMsgList: TIdMessageCollection; ACount: Integer): Boolean;
function RetrieveEnvelope(const AMsgNum: UInt32; AMsg: TIdMessage): Boolean;
function RetrieveEnvelopeRaw(const AMsgNum: UInt32; ADestList: TStrings): Boolean;
function RetrieveFlags(const AMsgNum: UInt32; var AFlags: TIdMessageFlagsSet): Boolean;
function RetrieveValue(const AMsgNum: UInt32; const AField: string; var AValue: string): Boolean;
function InternalRetrieveStructure(const AMsgNum: UInt32; AMsg: TIdMessage; AParts: TIdImapMessageParts): Boolean;
function RetrieveStructure(const AMsgNum: UInt32; AMsg: TIdMessage): Boolean;
function RetrievePart(const AMsgNum: UInt32; const APartNum: string; ADestStream: TStream; AContentTransferEncoding: string = 'text'): Boolean;
function RetrievePartPeek(const AMsgNum: UInt32; const APartNum: string; ADestStream: TStream; AContentTransferEncoding: string = 'text'): Boolean;
function RetrievePartToFile(const AMsgNum: UInt32; const APartNum: Integer; ALength: Integer; ADestFileNameAndPath: string; AContentTransferEncoding: string): Boolean;
function RetrievePartToFilePeek(const AMsgNum: UInt32; const APartNum: Integer; ALength: Integer; ADestFileNameAndPath: string; AContentTransferEncoding: string): Boolean;
function RetrieveText(const AMsgNum: UInt32; var AText: string): Boolean;
function RetrieveText2(const AMsgNum: UInt32; var AText: string): Boolean;
function RetrieveTextPeek(const AMsgNum: UInt32; var AText: string): Boolean;
function RetrieveTextPeek2(const AMsgNum: UInt32; var AText: string): Boolean;
function RetrieveHeader (const AMsgNum: UInt32; AMsg: TIdMessage): Boolean;
function RetrievePartHeader(const AMsgNum: UInt32; const APartNum: string; AHeaders: TIdHeaderList): Boolean;
function RetrieveMailBoxSize: Int64;
function RetrieveMsgSize(const AMsgNum: UInt32): Int64;
function RetrievePeek(const AMsgNum: UInt32; AMsg: TIdMessage): Boolean;
function GetUID(const AMsgNum: UInt32; var AUID: string): Boolean;
function UIDCopyMsg(const AMsgUID: String; const AMBName: String): Boolean;
function UIDCopyMsgs(const AMsgUIDList: TStrings; const AMBName: String): Boolean;
function UIDCheckMsgSeen(const AMsgUID: String): Boolean;
function UIDDeleteMsg(const AMsgUID: String): Boolean;
function UIDDeleteMsgs(const AMsgUIDList: array of String): Boolean;
function UIDRetrieveAllEnvelopes(AMsgList: TIdMessageCollection): Boolean;
function UIDRetrieve(const AMsgUID: String; AMsg: TIdMessage): Boolean;
function UIDRetrieveNoDecodeToFile(const AMsgUID: String; ADestFile: string): Boolean;
function UIDRetrieveNoDecodeToFilePeek(const AMsgUID: String; ADestFile: string): Boolean;
function UIDRetrieveNoDecodeToStream(const AMsgUID: String; AStream: TStream): Boolean;
function UIDRetrieveNoDecodeToStreamPeek(const AMsgUID: String; AStream: TStream): Boolean;
function UIDRetrieveEnvelope(const AMsgUID: String; AMsg: TIdMessage): Boolean;
function UIDRetrieveEnvelopeRaw(const AMsgUID: String; ADestList: TStrings): Boolean;
function UIDRetrieveFlags(const AMsgUID: String; var AFlags: TIdMessageFlagsSet): Boolean;
function UIDRetrieveValue(const AMsgUID: String; const AField: string; var AValue: string): Boolean;
function UIDInternalRetrieveStructure(const AMsgUID: String; AMsg: TIdMessage; AParts: TIdImapMessageParts): Boolean;
function UIDRetrieveStructure(const AMsgUID: String; AMsg: TIdMessage): Boolean;
function UIDRetrievePart(const AMsgUID: String; const APartNum: string; var ADestStream: TStream; AContentTransferEncoding: string = 'text'): Boolean;
function UIDRetrievePartPeek(const AMsgUID: String; const APartNum: string; var ADestStream: TStream; AContentTransferEncoding: string = 'text'): Boolean;
function UIDRetrievePartToFile(const AMsgUID: String; const APartNum: Integer; ALength: Integer; ADestFileNameAndPath: string; AContentTransferEncoding: string): Boolean;
function UIDRetrievePartToFilePeek(const AMsgUID: String; const APartNum: Integer; ALength: Integer; ADestFileNameAndPath: string; AContentTransferEncoding: string): Boolean;
function UIDRetrieveText(const AMsgUID: String; var AText: string): Boolean;
function UIDRetrieveText2(const AMsgUID: String; var AText: string): Boolean;
function UIDRetrieveTextPeek(const AMsgUID: String; var AText: string): Boolean;
function UIDRetrieveTextPeek2(const AMsgUID: String; var AText: string): Boolean;
function UIDRetrieveHeader(const AMsgUID: String; AMsg: TIdMessage): Boolean;
function UIDRetrievePartHeader(const AMsgUID: String; const APartNum: string; AHeaders: TIdHeaderList): Boolean;
function UIDRetrieveMailBoxSize: Int64;
function UIDRetrieveMsgSize(const AMsgUID: String): Int64;
function UIDRetrievePeek(const AMsgUID: String; AMsg: TIdMessage): Boolean;
function UIDSearchMailBox(const ASearchInfo: array of TIdIMAP4SearchRec; const ACharSet: String = ''): Boolean;
function UIDStoreFlags(const AMsgUID: String; const AStoreMethod: TIdIMAP4StoreDataItem; const AFlags: TIdMessageFlagsSet): Boolean;
function UIDStoreValue(const AMsgUID: String; const AStoreMethod: TIdIMAP4StoreDataItem; const AField, AValue: String): Boolean;
function UnsubscribeMailBox(const AMBName: String): Boolean;
function GetInternalResponse(const ATag: String; AExpectedResponses: array of String; ASingleLineMode: Boolean; ASingleLineMayBeSplit: Boolean = True): string;
function GetResponse: string;
function SendCmd(const AOut: string; AExpectedResponses: array of String; ASingleLineMode: Boolean = False; ASingleLineMayBeSplit: Boolean = True): string;
function ReadLnWait: string;
procedure WriteLn(const AOut: string = '');
procedure ProcessMessage(AMsg: TIdMessage; AHeaderOnly: Boolean = False);
procedure SendMsg(AMsg: TIdMessage; AHeadersOnly: Boolean = False);
function ConnectAndGetAll: string;
procedure CreateIOHandler(ABaseType: TIdIOHandlerClass = nil);
procedure CheckForGracefulDisconnect(ARaiseExceptionIfDisconnected: Boolean = True);
function CheckResponse(const AResponse: Int16; const AAllowedResponses: array of Int16): Int16;
function Connected: Boolean;
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
bool __fastcall Capability();
TIdIMAP4FolderTreatment * __fastcall FindHowServerCreatesFolders();
void __fastcall DoAlert(const UnicodeString AMsg);
bool __fastcall AppendMsg(const UnicodeString AMBName, TIdMessage * AMsg, const TIdMessageFlagsSet * AFlags = [], const System::TDateTime AInternalDateTimeGMT = 0.0);
bool __fastcall AppendMsgNoEncodeFromFile(const UnicodeString AMBName, UnicodeString ASourceFile, const TIdMessageFlagsSet * AFlags = [], const System::TDateTime AInternalDateTimeGMT = 0.0);
bool __fastcall AppendMsgNoEncodeFromStream(const UnicodeString AMBName, TStream * AStream, const TIdMessageFlagsSet * AFlags = [], const System::TDateTime AInternalDateTimeGMT = 0.0);
bool __fastcall CheckMailBox();
bool __fastcall CheckMsgSeen(const UInt32 AMsgNum);
void __fastcall Login();
bool __fastcall Connect(const bool AAutoLogin = true);
bool __fastcall CloseMailBox();
bool __fastcall CreateMailBox(const UnicodeString AMBName);
bool __fastcall DeleteMailBox(const UnicodeString AMBName);
bool __fastcall DeleteMsgs(const array of UInt32 AMsgNumList);
void __fastcall Disconnect(bool ANotifyPeer);
void __fastcall DisconnectNotifyPeer();
bool __fastcall ExamineMailBox(const UnicodeString AMBName, TIdMailBox * AMB);
bool __fastcall ExpungeMailBox();
void __fastcall KeepAlive();
bool __fastcall ListInferiorMailBoxes(TStrings * AMailBoxList, TStrings * AInferiorMailBoxList);
bool __fastcall ListMailBoxes(TStrings * AMailBoxList);
bool __fastcall ListSubscribedMailBoxes(TStrings * AMailBoxList);
bool __fastcall RenameMailBox(const UnicodeString AOldMBName, const UnicodeString ANewMBName);
bool __fastcall SearchMailBox(const array of TIdIMAP4SearchRec ASearchInfo, const UnicodeString ACharSet = '');
bool __fastcall SelectMailBox(const UnicodeString AMBName);
bool __fastcall StatusMailBox(const UnicodeString AMBName, TIdMailBox * AMB);
bool __fastcall StoreFlags(const array of UInt32 AMsgNumList, const TIdIMAP4StoreDataItem * AStoreMethod, const TIdMessageFlagsSet * AFlags);
bool __fastcall StoreValue(const array of UInt32 AMsgNumList, const TIdIMAP4StoreDataItem * AStoreMethod, const UnicodeString AField, const UnicodeString AValue);
bool __fastcall SubscribeMailBox(const UnicodeString AMBName);
bool __fastcall CopyMsg(const UInt32 AMsgNum, const UnicodeString AMBName);
bool __fastcall CopyMsgs(const array of UInt32 AMsgNumList, const UnicodeString AMBName);
bool __fastcall Retrieve(const UInt32 AMsgNum, TIdMessage * AMsg);
bool __fastcall RetrieveNoDecodeToFile(const UInt32 AMsgNum, UnicodeString ADestFile);
bool __fastcall RetrieveNoDecodeToFilePeek(const UInt32 AMsgNum, UnicodeString ADestFile);
bool __fastcall RetrieveNoDecodeToStream(const UInt32 AMsgNum, TStream * AStream);
bool __fastcall RetrieveNoDecodeToStreamPeek(const UInt32 AMsgNum, TStream * AStream);
bool __fastcall RetrieveAllEnvelopes(TIdMessageCollection * AMsgList);
bool __fastcall RetrieveAllHeaders(TIdMessageCollection * AMsgList);
bool __fastcall RetrieveFirstHeaders(TIdMessageCollection * AMsgList, int ACount);
bool __fastcall RetrieveAllMsgs(TIdMessageCollection * AMsgList);
bool __fastcall RetrieveFirstMsgs(TIdMessageCollection * AMsgList, int ACount);
bool __fastcall RetrieveEnvelope(const UInt32 AMsgNum, TIdMessage * AMsg);
bool __fastcall RetrieveEnvelopeRaw(const UInt32 AMsgNum, TStrings * ADestList);
bool __fastcall RetrieveFlags(const UInt32 AMsgNum, TIdMessageFlagsSet * &AFlags);
bool __fastcall RetrieveValue(const UInt32 AMsgNum, const UnicodeString AField, UnicodeString &AValue);
bool __fastcall InternalRetrieveStructure(const UInt32 AMsgNum, TIdMessage * AMsg, TIdImapMessageParts * AParts);
bool __fastcall RetrieveStructure(const UInt32 AMsgNum, TIdMessage * AMsg);
bool __fastcall RetrievePart(const UInt32 AMsgNum, const UnicodeString APartNum, TStream * ADestStream, UnicodeString AContentTransferEncoding = 'text');
bool __fastcall RetrievePartPeek(const UInt32 AMsgNum, const UnicodeString APartNum, TStream * ADestStream, UnicodeString AContentTransferEncoding = 'text');
bool __fastcall RetrievePartToFile(const UInt32 AMsgNum, const int APartNum, int ALength, UnicodeString ADestFileNameAndPath, UnicodeString AContentTransferEncoding);
bool __fastcall RetrievePartToFilePeek(const UInt32 AMsgNum, const int APartNum, int ALength, UnicodeString ADestFileNameAndPath, UnicodeString AContentTransferEncoding);
bool __fastcall RetrieveText(const UInt32 AMsgNum, UnicodeString &AText);
bool __fastcall RetrieveText2(const UInt32 AMsgNum, UnicodeString &AText);
bool __fastcall RetrieveTextPeek(const UInt32 AMsgNum, UnicodeString &AText);
bool __fastcall RetrieveTextPeek2(const UInt32 AMsgNum, UnicodeString &AText);
bool __fastcall RetrieveHeader(const UInt32 AMsgNum, TIdMessage * AMsg);
bool __fastcall RetrievePartHeader(const UInt32 AMsgNum, const UnicodeString APartNum, TIdHeaderList * AHeaders);
long long __fastcall RetrieveMailBoxSize();
long long __fastcall RetrieveMsgSize(const UInt32 AMsgNum);
bool __fastcall RetrievePeek(const UInt32 AMsgNum, TIdMessage * AMsg);
bool __fastcall GetUID(const UInt32 AMsgNum, UnicodeString &AUID);
bool __fastcall UIDCopyMsg(const UnicodeString AMsgUID, const UnicodeString AMBName);
bool __fastcall UIDCopyMsgs(const TStrings * AMsgUIDList, const UnicodeString AMBName);
bool __fastcall UIDCheckMsgSeen(const UnicodeString AMsgUID);
bool __fastcall UIDDeleteMsg(const UnicodeString AMsgUID);
bool __fastcall UIDDeleteMsgs(const array of String AMsgUIDList);
bool __fastcall UIDRetrieveAllEnvelopes(TIdMessageCollection * AMsgList);
bool __fastcall UIDRetrieve(const UnicodeString AMsgUID, TIdMessage * AMsg);
bool __fastcall UIDRetrieveNoDecodeToFile(const UnicodeString AMsgUID, UnicodeString ADestFile);
bool __fastcall UIDRetrieveNoDecodeToFilePeek(const UnicodeString AMsgUID, UnicodeString ADestFile);
bool __fastcall UIDRetrieveNoDecodeToStream(const UnicodeString AMsgUID, TStream * AStream);
bool __fastcall UIDRetrieveNoDecodeToStreamPeek(const UnicodeString AMsgUID, TStream * AStream);
bool __fastcall UIDRetrieveEnvelope(const UnicodeString AMsgUID, TIdMessage * AMsg);
bool __fastcall UIDRetrieveEnvelopeRaw(const UnicodeString AMsgUID, TStrings * ADestList);
bool __fastcall UIDRetrieveFlags(const UnicodeString AMsgUID, TIdMessageFlagsSet * &AFlags);
bool __fastcall UIDRetrieveValue(const UnicodeString AMsgUID, const UnicodeString AField, UnicodeString &AValue);
bool __fastcall UIDInternalRetrieveStructure(const UnicodeString AMsgUID, TIdMessage * AMsg, TIdImapMessageParts * AParts);
bool __fastcall UIDRetrieveStructure(const UnicodeString AMsgUID, TIdMessage * AMsg);
bool __fastcall UIDRetrievePart(const UnicodeString AMsgUID, const UnicodeString APartNum, TStream * &ADestStream, UnicodeString AContentTransferEncoding = 'text');
bool __fastcall UIDRetrievePartPeek(const UnicodeString AMsgUID, const UnicodeString APartNum, TStream * &ADestStream, UnicodeString AContentTransferEncoding = 'text');
bool __fastcall UIDRetrievePartToFile(const UnicodeString AMsgUID, const int APartNum, int ALength, UnicodeString ADestFileNameAndPath, UnicodeString AContentTransferEncoding);
bool __fastcall UIDRetrievePartToFilePeek(const UnicodeString AMsgUID, const int APartNum, int ALength, UnicodeString ADestFileNameAndPath, UnicodeString AContentTransferEncoding);
bool __fastcall UIDRetrieveText(const UnicodeString AMsgUID, UnicodeString &AText);
bool __fastcall UIDRetrieveText2(const UnicodeString AMsgUID, UnicodeString &AText);
bool __fastcall UIDRetrieveTextPeek(const UnicodeString AMsgUID, UnicodeString &AText);
bool __fastcall UIDRetrieveTextPeek2(const UnicodeString AMsgUID, UnicodeString &AText);
bool __fastcall UIDRetrieveHeader(const UnicodeString AMsgUID, TIdMessage * AMsg);
bool __fastcall UIDRetrievePartHeader(const UnicodeString AMsgUID, const UnicodeString APartNum, TIdHeaderList * AHeaders);
long long __fastcall UIDRetrieveMailBoxSize();
long long __fastcall UIDRetrieveMsgSize(const UnicodeString AMsgUID);
bool __fastcall UIDRetrievePeek(const UnicodeString AMsgUID, TIdMessage * AMsg);
bool __fastcall UIDSearchMailBox(const array of TIdIMAP4SearchRec ASearchInfo, const UnicodeString ACharSet = '');
bool __fastcall UIDStoreFlags(const UnicodeString AMsgUID, const TIdIMAP4StoreDataItem * AStoreMethod, const TIdMessageFlagsSet * AFlags);
bool __fastcall UIDStoreValue(const UnicodeString AMsgUID, const TIdIMAP4StoreDataItem * AStoreMethod, const UnicodeString AField, const UnicodeString AValue);
bool __fastcall UnsubscribeMailBox(const UnicodeString AMBName);
UnicodeString __fastcall GetInternalResponse(const UnicodeString ATag, array of String AExpectedResponses, bool ASingleLineMode, bool ASingleLineMayBeSplit = True);
UnicodeString __fastcall GetResponse();
UnicodeString __fastcall SendCmd(const UnicodeString AOut, array of String AExpectedResponses, bool ASingleLineMode = False, bool ASingleLineMayBeSplit = True);
UnicodeString __fastcall ReadLnWait();
void __fastcall WriteLn(const UnicodeString AOut = '');
void __fastcall ProcessMessage(TIdMessage * AMsg, bool AHeaderOnly = False);
void __fastcall SendMsg(TIdMessage * AMsg, bool AHeadersOnly = False);
UnicodeString __fastcall ConnectAndGetAll();
void __fastcall CreateIOHandler(TIdIOHandlerClass * ABaseType = nil);
void __fastcall CheckForGracefulDisconnect(bool ARaiseExceptionIfDisconnected = True);
Int16 __fastcall CheckResponse(const Int16 AResponse, const array of Int16 AAllowedResponses);
bool __fastcall Connected();
void __fastcall RaiseExceptionForLastCmdResult();
void __fastcall WriteHeader(TStrings * AHeader);
void __fastcall WriteRFCStrings(TStrings * AStrings);
void __fastcall BeginWork(TWorkMode * AWorkMode, const long long ASize = 0);
void __fastcall DoWork(TWorkMode * AWorkMode, const long long ACount);
void __fastcall EndWork(TWorkMode * AWorkMode);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

