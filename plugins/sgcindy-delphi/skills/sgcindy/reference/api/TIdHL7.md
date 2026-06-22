# TIdHL7

unit: IdHL7

Add `IdHL7` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `ObjTag: TObject` | `TObject` | `__property TObject * ObjTag;` |
| `Status: TIdHL7Status (read-only)` | [TIdHL7Status](../types/TIdHL7Status.md) | `__property TIdHL7Status * Status /* read-only */;` |
| `StatusDesc: String (read-only)` | `String` | `__property UnicodeString StatusDesc /* read-only */;` |
| `IsServer: Boolean (read-only)` | `Boolean` | `__property bool IsServer /* read-only */;` |
| `DefStringEncoding: IIdTextEncoding` | [IIdTextEncoding](../types/IIdTextEncoding.md) | `__property IIdTextEncoding DefStringEncoding;` |
| `DefAnsiEncoding: IIdTextEncoding` | [IIdTextEncoding](../types/IIdTextEncoding.md) | `__property IIdTextEncoding DefAnsiEncoding;` |
| `IsServerExecuting: Boolean (read-only)` | `Boolean` | `__property bool IsServerExecuting /* read-only */;` |
| `Address: String` | `String` | `__property UnicodeString Address;` |
| `Port: Word` | `Word` | `__property unsigned short Port;` |
| `KeepAlive: TIdHL7KeepAlive` | [TIdHL7KeepAlive](../types/TIdHL7KeepAlive.md) | `__property TIdHL7KeepAlive * KeepAlive;` |
| `TimeOut: UInt32` | `UInt32` | `__property UInt32 TimeOut;` |
| `ReceiveTimeout: LongWord` | `LongWord` | `__property unsigned int ReceiveTimeout;` |
| `ConnectionLimit: Word` | `Word` | `__property unsigned short ConnectionLimit;` |
| `IPRestriction: String` | `String` | `__property UnicodeString IPRestriction;` |
| `IPMask: String` | `String` | `__property UnicodeString IPMask;` |
| `ReconnectDelay: LongWord` | `LongWord` | `__property unsigned int ReconnectDelay;` |
| `ConnectionTimeout: UInt32` | `UInt32` | `__property UInt32 ConnectionTimeout;` |
| `CommunicationMode: THL7CommunicationMode` | [THL7CommunicationMode](../types/THL7CommunicationMode.md) | `__property THL7CommunicationMode * CommunicationMode;` |
| `IsListener: Boolean` | `Boolean` | `__property bool IsListener;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnMessageArrive: TMessageArriveEvent` | [TMessageArriveEvent](../types/TMessageArriveEvent.md) | `__property TMessageArriveEvent OnMessageArrive;` |
| `OnReceiveMessage: TMessageReceiveEvent` | [TMessageReceiveEvent](../types/TMessageReceiveEvent.md) | `__property TMessageReceiveEvent OnReceiveMessage;` |
| `OnConnect: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnConnect;` |
| `OnDisconnect: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDisconnect;` |
| `OnConnCountChange: TIdHL7ConnCountEvent` | [TIdHL7ConnCountEvent](../types/TIdHL7ConnCountEvent.md) | `__property TIdHL7ConnCountEvent OnConnCountChange;` |
| `OnReceiveError: TReceiveErrorEvent` | [TReceiveErrorEvent](../types/TReceiveErrorEvent.md) | `__property TReceiveErrorEvent OnReceiveError;` |

## Methods

Delphi

```pascal
procedure EnforceWaitReplyTimeout;
function Going: Boolean;
function Connected: Boolean;
procedure Start;
procedure PreStop;
procedure Stop;
procedure WaitForConnection(AMaxLength: UInt32);
function AsynchronousSend(const AMsg: String; ASyncConnection: TIdTCPConnection = nil): TSendResponse;
function SynchronousSend(const AMsg: String; var VReply: String): TSendResponse;
procedure CheckSynchronousSendResult(AResult: TSendResponse; const AMsg: String);
procedure SendMessage(const AMsg: String);
function GetReply(var VReply: String): TSendResponse;
function GetMessage(var VMsg: String): IInterface;
procedure SendReply(AMsgHnd: IInterface; const AReply: String);
function HasClientConnection : Boolean;
procedure Disconnect;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall EnforceWaitReplyTimeout();
bool __fastcall Going();
bool __fastcall Connected();
void __fastcall Start();
void __fastcall PreStop();
void __fastcall Stop();
void __fastcall WaitForConnection(UInt32 AMaxLength);
TSendResponse * __fastcall AsynchronousSend(const UnicodeString AMsg, TIdTCPConnection * ASyncConnection = nil);
TSendResponse * __fastcall SynchronousSend(const UnicodeString AMsg, UnicodeString &VReply);
void __fastcall CheckSynchronousSendResult(TSendResponse * AResult, const UnicodeString AMsg);
void __fastcall SendMessage(const UnicodeString AMsg);
TSendResponse * __fastcall GetReply(UnicodeString &VReply);
IInterface __fastcall GetMessage(UnicodeString &VMsg);
void __fastcall SendReply(IInterface AMsgHnd, const UnicodeString AReply);
bool __fastcall HasClientConnection();
void __fastcall Disconnect();
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

