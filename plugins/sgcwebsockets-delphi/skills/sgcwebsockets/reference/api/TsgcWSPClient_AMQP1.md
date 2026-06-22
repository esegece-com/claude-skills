# TsgcWSPClient_AMQP1

unit: sgcWebSocket_Protocols
Edition: requires SGC_AMQP1

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `AMQPOptions: TsgcAMQP1Options` | [TsgcAMQP1Options](../types/TsgcAMQP1Options.md) | `__property TsgcAMQP1Options * AMQPOptions;` |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Broker: TsgcWSProtocol_Broker_Client` | [TsgcWSProtocol_Broker_Client](../types/TsgcWSProtocol_Broker_Client.md) | `__property TsgcWSProtocol_Broker_Client * Broker;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `ConnectionState: TsgcAMQP1ConnectionState (read-only)` | [TsgcAMQP1ConnectionState](../types/TsgcAMQP1ConnectionState.md) | `__property TsgcAMQP1ConnectionState * ConnectionState /* read-only */;` |
| `Protocol: string (read-only)` | `string` | `__property UnicodeString Protocol /* read-only */;` |
| `MsgType: TwsProtocolMessage` | [TwsProtocolMessage](../types/TwsProtocolMessage.md) | `__property TwsProtocolMessage * MsgType;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnAMQPBeforeReadFrame: TsgcAMQP1BeforeReadFrameEvent` | [TsgcAMQP1BeforeReadFrameEvent](../types/TsgcAMQP1BeforeReadFrameEvent.md) | `__property TsgcAMQP1BeforeReadFrameEvent OnAMQPBeforeReadFrame;` |
| `OnAMQPBeforeWriteFrame: TsgcAMQP1BeforeWriteFrameEvent` | [TsgcAMQP1BeforeWriteFrameEvent](../types/TsgcAMQP1BeforeWriteFrameEvent.md) | `__property TsgcAMQP1BeforeWriteFrameEvent OnAMQPBeforeWriteFrame;` |
| `OnAMQPConnect: TsgcAMQP1ConnectEvent` | [TsgcAMQP1ConnectEvent](../types/TsgcAMQP1ConnectEvent.md) | `__property TsgcAMQP1ConnectEvent OnAMQPConnect;` |
| `OnAMQPSASLAuthentication: TsgcAMQP1SASLAuthenticationEvent` | [TsgcAMQP1SASLAuthenticationEvent](../types/TsgcAMQP1SASLAuthenticationEvent.md) | `__property TsgcAMQP1SASLAuthenticationEvent OnAMQPSASLAuthentication;` |
| `OnAMQPMessage: TsgcAMQP1MessagenEvent` | [TsgcAMQP1MessagenEvent](../types/TsgcAMQP1MessagenEvent.md) | `__property TsgcAMQP1MessagenEvent OnAMQPMessage;` |
| `OnAMQPMessageSent: TsgcAMQP1MessageSentEvent` | [TsgcAMQP1MessageSentEvent](../types/TsgcAMQP1MessageSentEvent.md) | `__property TsgcAMQP1MessageSentEvent OnAMQPMessageSent;` |
| `OnAMQPMessageSentAck: TsgcAMQP1MessageSentAckEvent` | [TsgcAMQP1MessageSentAckEvent](../types/TsgcAMQP1MessageSentAckEvent.md) | `__property TsgcAMQP1MessageSentAckEvent OnAMQPMessageSentAck;` |
| `OnAMQPSessionOpen: TsgcAMQP1SessionOpenEvent` | [TsgcAMQP1SessionOpenEvent](../types/TsgcAMQP1SessionOpenEvent.md) | `__property TsgcAMQP1SessionOpenEvent OnAMQPSessionOpen;` |
| `OnAMQPSessionClose: TsgcAMQP1SessionCloseEvent` | [TsgcAMQP1SessionCloseEvent](../types/TsgcAMQP1SessionCloseEvent.md) | `__property TsgcAMQP1SessionCloseEvent OnAMQPSessionClose;` |
| `OnAMQPLinkOpen: TsgcAMQP1LinkOpenEvent` | [TsgcAMQP1LinkOpenEvent](../types/TsgcAMQP1LinkOpenEvent.md) | `__property TsgcAMQP1LinkOpenEvent OnAMQPLinkOpen;` |
| `OnAMQPLinkClose: TsgcAMQP1LinkCloseEvent` | [TsgcAMQP1LinkCloseEvent](../types/TsgcAMQP1LinkCloseEvent.md) | `__property TsgcAMQP1LinkCloseEvent OnAMQPLinkClose;` |
| `OnAMQPClose: TsgcAMQP1CloseEvent` | [TsgcAMQP1CloseEvent](../types/TsgcAMQP1CloseEvent.md) | `__property TsgcAMQP1CloseEvent OnAMQPClose;` |
| `OnAMQPException: TsgcAMQP1ExceptionEvent` | [TsgcAMQP1ExceptionEvent](../types/TsgcAMQP1ExceptionEvent.md) | `__property TsgcAMQP1ExceptionEvent OnAMQPException;` |
| `OnAMQPDisconnect: TsgcAMQP1DisconnectEvent` | [TsgcAMQP1DisconnectEvent](../types/TsgcAMQP1DisconnectEvent.md) | `__property TsgcAMQP1DisconnectEvent OnAMQPDisconnect;` |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
function CreateSession(const aName: string = ''; const aOptions: TsgcAMQP1MethodOptions_SessionOpen = nil) : TsgcAMQP1Session;
function CloseSession(const aName: string; const aOptions: TsgcAMQP1MethodOptions_SessionClose = nil): Boolean;
function PutCBSToken(const aLink: TsgcAMQP1SenderLink; const aName, aTokenType, aToken: string; const aExpiration: Integer = 3600; aTimeout: Integer = 10000): Boolean;
function CreateCBSLink(const aName: string; const aSession: string = '') : TsgcAMQP1SenderLink;
function CreateAzureCbsSasToken(const aName, aNameSpace, aEntityName, aKeyName, aKeyValue: string; const aExpiration: Integer = 3600; aTimeout: Integer = 10000; aRaiseIfError: Boolean = False): Boolean;
function CreateAzureCbsJWT(const aName, aNameSpace, aEntityName, aTenant, aApplicationId, aSecret: string; aListeningPort: Integer = 8080; const aExpiration: Integer = 3600; aTimeout: Integer = 10000; aRaiseIfError: Boolean = False): Boolean;
function CreateSenderLink(const aSession: string; const aName: string = ''; const aTarget: string = ''; const aOptions: TsgcAMQP1MethodOptions_CreateSenderLink = nil) : TsgcAMQP1SenderLink;
function CreateReceiverLink(const aSession: string; const aName: string = ''; const aSource: string = ''; const aOptions: TsgcAMQP1MethodOptions_CreateReceiverLink = nil) : TsgcAMQP1ReceiverLink;
function CloseLink(const aSession, aName: string; const aOptions: TsgcAMQP1MethodOptions_CloseLink = nil): Boolean;
function GetMessage(const aSession, aLink: string; aTimeout: Integer = 10000): Boolean;
procedure Ping;
procedure Close(const aOptions: TsgcAMQP1MethodOptions_Close = nil);
procedure DoAMQPBeforeReadFrameEvent(const aFrame: TsgcAMQP1Frame; var Handled: Boolean);
procedure DoAMQPBeforeWriteFrameEvent(const aFrame: TsgcAMQP1Frame; var Handled: Boolean);
procedure DoAMQPConnectEvent(const aOpen: TsgcAMQP1FrameOpen);
procedure DoAMQPCloseEvent(const aError: TsgcAMQP1FrameError);
procedure DoAMQPSASLAuthenticationEvent(aCode: TsgcAMQP1SaslCode; const aDescription: string; var Handled: Boolean);
procedure DoAMQPExceptionEvent(E: Exception);
procedure DoAMQPSessionOpenEvent(const aSession: TsgcAMQP1Session; const aBegin: TsgcAMQP1FrameBegin);
procedure DoAMQPSessionCloseEvent(const aSession: TsgcAMQP1Session; const aEnd: TsgcAMQP1FrameEnd);
procedure DoAMQPMessageEvent(const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1ReceiverLink; const aMessage: TsgcAMQP1Message; var DeliveryState: TsgcAMQP1MessageDeliveryState);
procedure DoAMQPMessageSentEvent(const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1SenderLink; const aMessageId: string);
procedure DoAMQPMessageSentAckEvent(const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1SenderLink; const aMessageId: string; const aDeliveryState: TsgcAMQP1FrameDeliveryStates; const aDisposition: TsgcAMQP1FrameDisposition);
procedure DoAMQPLinkCloseEvent(const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1Link; const aDetach: TsgcAMQP1FrameDetach);
procedure DoAMQPLinkOpenEvent(const aSession: TsgcAMQP1Session; const aLink: TsgcAMQP1Link; const aAttach: TsgcAMQP1FrameAttach);
procedure DoAMQPDisconnectEvent(aCode: Integer);
procedure WriteData(const aText: String);
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
TsgcAMQP1Session * __fastcall CreateSession(const UnicodeString aName = '', const TsgcAMQP1MethodOptions_SessionOpen * aOptions = nil);
bool __fastcall CloseSession(const UnicodeString aName, const TsgcAMQP1MethodOptions_SessionClose * aOptions = nil);
bool __fastcall PutCBSToken(const TsgcAMQP1SenderLink * aLink, const UnicodeString aName, const UnicodeString aTokenType, const UnicodeString aToken, const int aExpiration = 3600, int aTimeout = 10000);
TsgcAMQP1SenderLink * __fastcall CreateCBSLink(const UnicodeString aName, const UnicodeString aSession = '');
bool __fastcall CreateAzureCbsSasToken(const UnicodeString aName, const UnicodeString aNameSpace, const UnicodeString aEntityName, const UnicodeString aKeyName, const UnicodeString aKeyValue, const int aExpiration = 3600, int aTimeout = 10000, bool aRaiseIfError = False);
bool __fastcall CreateAzureCbsJWT(const UnicodeString aName, const UnicodeString aNameSpace, const UnicodeString aEntityName, const UnicodeString aTenant, const UnicodeString aApplicationId, const UnicodeString aSecret, int aListeningPort = 8080, const int aExpiration = 3600, int aTimeout = 10000, bool aRaiseIfError = False);
TsgcAMQP1SenderLink * __fastcall CreateSenderLink(const UnicodeString aSession, const UnicodeString aName = '', const UnicodeString aTarget = '', const TsgcAMQP1MethodOptions_CreateSenderLink * aOptions = nil);
TsgcAMQP1ReceiverLink * __fastcall CreateReceiverLink(const UnicodeString aSession, const UnicodeString aName = '', const UnicodeString aSource = '', const TsgcAMQP1MethodOptions_CreateReceiverLink * aOptions = nil);
bool __fastcall CloseLink(const UnicodeString aSession, const UnicodeString aName, const TsgcAMQP1MethodOptions_CloseLink * aOptions = nil);
bool __fastcall GetMessage(const UnicodeString aSession, const UnicodeString aLink, int aTimeout = 10000);
void __fastcall Ping();
void __fastcall Close(const TsgcAMQP1MethodOptions_Close * aOptions = nil);
void __fastcall DoAMQPBeforeReadFrameEvent(const TsgcAMQP1Frame * aFrame, bool &Handled);
void __fastcall DoAMQPBeforeWriteFrameEvent(const TsgcAMQP1Frame * aFrame, bool &Handled);
void __fastcall DoAMQPConnectEvent(const TsgcAMQP1FrameOpen * aOpen);
void __fastcall DoAMQPCloseEvent(const TsgcAMQP1FrameError * aError);
void __fastcall DoAMQPSASLAuthenticationEvent(TsgcAMQP1SaslCode * aCode, const UnicodeString aDescription, bool &Handled);
void __fastcall DoAMQPExceptionEvent(Exception E);
void __fastcall DoAMQPSessionOpenEvent(const TsgcAMQP1Session * aSession, const TsgcAMQP1FrameBegin * aBegin);
void __fastcall DoAMQPSessionCloseEvent(const TsgcAMQP1Session * aSession, const TsgcAMQP1FrameEnd * aEnd);
void __fastcall DoAMQPMessageEvent(const TsgcAMQP1Session * aSession, const TsgcAMQP1ReceiverLink * aLink, const TsgcAMQP1Message * aMessage, TsgcAMQP1MessageDeliveryState * &DeliveryState);
void __fastcall DoAMQPMessageSentEvent(const TsgcAMQP1Session * aSession, const TsgcAMQP1SenderLink * aLink, const UnicodeString aMessageId);
void __fastcall DoAMQPMessageSentAckEvent(const TsgcAMQP1Session * aSession, const TsgcAMQP1SenderLink * aLink, const UnicodeString aMessageId, const TsgcAMQP1FrameDeliveryStates * aDeliveryState, const TsgcAMQP1FrameDisposition * aDisposition);
void __fastcall DoAMQPLinkCloseEvent(const TsgcAMQP1Session * aSession, const TsgcAMQP1Link * aLink, const TsgcAMQP1FrameDetach * aDetach);
void __fastcall DoAMQPLinkOpenEvent(const TsgcAMQP1Session * aSession, const TsgcAMQP1Link * aLink, const TsgcAMQP1FrameAttach * aAttach);
void __fastcall DoAMQPDisconnectEvent(int aCode);
void __fastcall WriteData(const UnicodeString aText);
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

