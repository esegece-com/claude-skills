# TsgcWSPClient_AMQP

unit: sgcWebSocket_Protocols
Edition: Standard

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `AMQPOptions: TsgcWSAMQP_Options` | [TsgcWSAMQP_Options](../types/TsgcWSAMQP_Options.md) | `__property TsgcWSAMQP_Options * AMQPOptions;` |
| `HeartBeat: TsgcWSAMQPHeartBeat_Options` | [TsgcWSAMQPHeartBeat_Options](../types/TsgcWSAMQPHeartBeat_Options.md) | `__property TsgcWSAMQPHeartBeat_Options * HeartBeat;` |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Broker: TsgcWSProtocol_Broker_Client` | [TsgcWSProtocol_Broker_Client](../types/TsgcWSProtocol_Broker_Client.md) | `__property TsgcWSProtocol_Broker_Client * Broker;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `Channels: TsgcAMQPChannelThreads (read-only)` | [TsgcAMQPChannelThreads](../types/TsgcAMQPChannelThreads.md) | `__property TsgcAMQPChannelThreads * Channels /* read-only */;` |
| `Authentication: TsgcWSAMQPAuthentication_Options` | [TsgcWSAMQPAuthentication_Options](../types/TsgcWSAMQPAuthentication_Options.md) | `__property TsgcWSAMQPAuthentication_Options * Authentication;` |
| `Protocol: string (read-only)` | `string` | `__property UnicodeString Protocol /* read-only */;` |
| `MsgType: TwsProtocolMessage` | [TwsProtocolMessage](../types/TwsProtocolMessage.md) | `__property TwsProtocolMessage * MsgType;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnAMQPConnect: TsgcAMQPConnectEvent` | [TsgcAMQPConnectEvent](../types/TsgcAMQPConnectEvent.md) | `__property TsgcAMQPConnectEvent OnAMQPConnect;` |
| `OnAMQPAuthentication: TsgcAMQPAuthenticationEvent` | [TsgcAMQPAuthenticationEvent](../types/TsgcAMQPAuthenticationEvent.md) | `__property TsgcAMQPAuthenticationEvent OnAMQPAuthentication;` |
| `OnAMQPChallenge: TsgcAMQPChallengeEvent` | [TsgcAMQPChallengeEvent](../types/TsgcAMQPChallengeEvent.md) | `__property TsgcAMQPChallengeEvent OnAMQPChallenge;` |
| `OnAMQPHeartBeat: TsgcAMQPHeartBeatEvent` | [TsgcAMQPHeartBeatEvent](../types/TsgcAMQPHeartBeatEvent.md) | `__property TsgcAMQPHeartBeatEvent OnAMQPHeartBeat;` |
| `OnAMQPChannelOpen: TsgcAMQPChannelOpenEvent` | [TsgcAMQPChannelOpenEvent](../types/TsgcAMQPChannelOpenEvent.md) | `__property TsgcAMQPChannelOpenEvent OnAMQPChannelOpen;` |
| `OnAMQPChannelClose: TsgcAMQPChannelCloseEvent` | [TsgcAMQPChannelCloseEvent](../types/TsgcAMQPChannelCloseEvent.md) | `__property TsgcAMQPChannelCloseEvent OnAMQPChannelClose;` |
| `OnAMQPChannelFlow: TsgcAMQPChannelFlowEvent` | [TsgcAMQPChannelFlowEvent](../types/TsgcAMQPChannelFlowEvent.md) | `__property TsgcAMQPChannelFlowEvent OnAMQPChannelFlow;` |
| `OnAMQPExchangeDeclare: TsgcAMQPExchangeDeclareEvent` | [TsgcAMQPExchangeDeclareEvent](../types/TsgcAMQPExchangeDeclareEvent.md) | `__property TsgcAMQPExchangeDeclareEvent OnAMQPExchangeDeclare;` |
| `OnAMQPExchangeDelete: TsgcAMQPExchangeDeleteEvent` | [TsgcAMQPExchangeDeleteEvent](../types/TsgcAMQPExchangeDeleteEvent.md) | `__property TsgcAMQPExchangeDeleteEvent OnAMQPExchangeDelete;` |
| `OnAMQPQueueDeclare: TsgcAMQPQueueDeclareEvent` | [TsgcAMQPQueueDeclareEvent](../types/TsgcAMQPQueueDeclareEvent.md) | `__property TsgcAMQPQueueDeclareEvent OnAMQPQueueDeclare;` |
| `OnAMQPQueueBind: TsgcAMQPQueueBindEvent` | [TsgcAMQPQueueBindEvent](../types/TsgcAMQPQueueBindEvent.md) | `__property TsgcAMQPQueueBindEvent OnAMQPQueueBind;` |
| `OnAMQPQueueUnBind: TsgcAMQPQueueUnBindEvent` | [TsgcAMQPQueueUnBindEvent](../types/TsgcAMQPQueueUnBindEvent.md) | `__property TsgcAMQPQueueUnBindEvent OnAMQPQueueUnBind;` |
| `OnAMQPQueuePurge: TsgcAMQPQueuePurgeEvent` | [TsgcAMQPQueuePurgeEvent](../types/TsgcAMQPQueuePurgeEvent.md) | `__property TsgcAMQPQueuePurgeEvent OnAMQPQueuePurge;` |
| `OnAMQPQueueDelete: TsgcAMQPQueueDeleteEvent` | [TsgcAMQPQueueDeleteEvent](../types/TsgcAMQPQueueDeleteEvent.md) | `__property TsgcAMQPQueueDeleteEvent OnAMQPQueueDelete;` |
| `OnAMQPBasicQoS: TsgcAMQPBasicQoSEvent` | [TsgcAMQPBasicQoSEvent](../types/TsgcAMQPBasicQoSEvent.md) | `__property TsgcAMQPBasicQoSEvent OnAMQPBasicQoS;` |
| `OnAMQPBasicConsume: TsgcAMQPBasicConsumeEvent` | [TsgcAMQPBasicConsumeEvent](../types/TsgcAMQPBasicConsumeEvent.md) | `__property TsgcAMQPBasicConsumeEvent OnAMQPBasicConsume;` |
| `OnAMQPBasicCancelConsume: TsgcAMQPBasicCancelConsumeEvent` | [TsgcAMQPBasicCancelConsumeEvent](../types/TsgcAMQPBasicCancelConsumeEvent.md) | `__property TsgcAMQPBasicCancelConsumeEvent OnAMQPBasicCancelConsume;` |
| `OnAMQPBasicReturn: TsgcAMQPBasicReturnEvent` | [TsgcAMQPBasicReturnEvent](../types/TsgcAMQPBasicReturnEvent.md) | `__property TsgcAMQPBasicReturnEvent OnAMQPBasicReturn;` |
| `OnAMQPBasicDeliver: TsgcAMQPBasicDeliverEvent` | [TsgcAMQPBasicDeliverEvent](../types/TsgcAMQPBasicDeliverEvent.md) | `__property TsgcAMQPBasicDeliverEvent OnAMQPBasicDeliver;` |
| `OnAMQPBasicGetOk: TsgcAMQPBasicGetOkEvent` | [TsgcAMQPBasicGetOkEvent](../types/TsgcAMQPBasicGetOkEvent.md) | `__property TsgcAMQPBasicGetOkEvent OnAMQPBasicGetOk;` |
| `OnAMQPBasicGetEmpty: TsgcAMQPBasicGetEmptyEvent` | [TsgcAMQPBasicGetEmptyEvent](../types/TsgcAMQPBasicGetEmptyEvent.md) | `__property TsgcAMQPBasicGetEmptyEvent OnAMQPBasicGetEmpty;` |
| `OnAMQPBasicRecoverOk: TsgcAMQPBasicRecoverOkEvent` | [TsgcAMQPBasicRecoverOkEvent](../types/TsgcAMQPBasicRecoverOkEvent.md) | `__property TsgcAMQPBasicRecoverOkEvent OnAMQPBasicRecoverOk;` |
| `OnAMQPTransactionOk: TsgcAMQPTransactionOkEvent` | [TsgcAMQPTransactionOkEvent](../types/TsgcAMQPTransactionOkEvent.md) | `__property TsgcAMQPTransactionOkEvent OnAMQPTransactionOk;` |
| `OnAMQPDisconnect: TsgcAMQPDisconnectEvent` | [TsgcAMQPDisconnectEvent](../types/TsgcAMQPDisconnectEvent.md) | `__property TsgcAMQPDisconnectEvent OnAMQPDisconnect;` |
| `OnAMQPException: TsgcAMQPExceptionEvent` | [TsgcAMQPExceptionEvent](../types/TsgcAMQPExceptionEvent.md) | `__property TsgcAMQPExceptionEvent OnAMQPException;` |
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
procedure Close(aReplyCode: Word; const aReplyText: string; aFailClassId: TsgcAMQPClass = amqpClassNone; aFailMethodId: TsgcAMQPMethod = amqpMethodNone);
function CloseEx(aReplyCode: Word; const aReplyText: string; aFailClassId: TsgcAMQPClass = amqpClassNone; aFailMethodId: TsgcAMQPMethod = amqpMethodNone): Boolean;
procedure OpenChannel(const aChannel: string);
function OpenChannelEx(const aChannel: string; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT): Boolean;
procedure CloseChannel(const aChannel: string; aReplyCode: Word = 0; const aReplyText: string = ''; aFailClassId: TsgcAMQPClass = amqpClassNone; aFailMethodId: TsgcAMQPMethod = amqpMethodNone);
function CloseChannelEx(const aChannel: string; aReplyCode: Word = 0; const aReplyText: string = ''; aFailClassId: TsgcAMQPClass = amqpClassNone; aFailMethodId: TsgcAMQPMethod = amqpMethodNone; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT): Boolean;
procedure EnableChannel(const aChannel: string);
function EnableChannelEx(const aChannel: string; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT): Boolean;
procedure DisableChannel(const aChannel: string);
function DisableChannelEx(const aChannel: string; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT): Boolean;
procedure DeclareExchange(const aChannel, aExchange: string; const aExchangeType: string = 'direct'; aPassive: Boolean = false; aDurable: Boolean = false; aAutoDelete: Boolean = false; aInternal: Boolean = false; aNoWait: Boolean = false; const aArguments: string = '');
function DeclareExchangeEx(const aChannel, aExchange: string; const aExchangeType: string = 'direct'; aPassive: Boolean = false; aDurable: Boolean = false; aAutoDelete: Boolean = false; aInternal: Boolean = false; aNoWait: Boolean = false; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT; const aArguments: string = ''): Boolean;
procedure DeleteExchange(const aChannel, aExchange: string; aIfUnused: Boolean = false; aNoWait: Boolean = false);
function DeleteExchangeEx(const aChannel, aExchange: string; aIfUnused: Boolean = false; aNoWait: Boolean = false; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT): Boolean;
procedure DeclareQueue(const aChannel, aQueue: string; aPassive: Boolean = false; aDurable: Boolean = false; aExclusive: Boolean = false; aAutoDelete: Boolean = false; aNoWait: Boolean = false; const aArguments: string = '');
function DeclareQueueEx(const aChannel, aQueue: string; aPassive: Boolean = false; aDurable: Boolean = false; aExclusive: Boolean = false; aAutoDelete: Boolean = false; aNoWait: Boolean = false; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT; const aArguments: string = ''): Boolean;
procedure BindQueue(const aChannel, aQueue, aExchange, aRoutingKey: string; aNoWait: Boolean = false; const aArguments: string = '');
function BindQueueEx(const aChannel, aQueue, aExchange, aRoutingKey: string; aNoWait: Boolean = false; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT; const aArguments: string = ''): Boolean;
procedure UnBindQueue(const aChannel, aQueue, aExchange, aRoutingKey: string; const aArguments: string = '');
function UnBindQueueEx(const aChannel, aQueue, aExchange, aRoutingKey: string; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT; const aArguments: string = ''): Boolean;
procedure PurgeQueue(const aChannel, aQueue: string; aNoWait: Boolean = false);
function PurgeQueueEx(const aChannel, aQueue: string; aNoWait: Boolean = false; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT): Boolean;
procedure DeleteQueue(const aChannel, aQueue: string; aIfUnused: Boolean = false; aIfEmpty: Boolean = false; aNoWait: Boolean = false);
function DeleteQueueEx(const aChannel, aQueue: string; aIfUnused: Boolean = false; aIfEmpty: Boolean = false; aNoWait: Boolean = false; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT): Boolean;
procedure SetQoS(const aChannel: string; aPrefetchSize: Cardinal = 0; aPrefetchCount: Word = 0; aGlobal: Boolean = false);
function SetQoSEx(const aChannel: string; aPrefetchSize: Cardinal = 0; aPrefetchCount: Word = 0; aGlobal: Boolean = false; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT): Boolean;
procedure Consume(const aChannel, aQueue: string; const aConsumerTag: string = ''; aNoLocal: Boolean = false; aNoAck: Boolean = false; aExclusive: Boolean = false; aNoWait: Boolean = false; const aArguments: string = '');
function ConsumeEx(const aChannel, aQueue: string; const aConsumerTag: string = ''; aNoLocal: Boolean = false; aNoAck: Boolean = false; aExclusive: Boolean = false; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT; const aArguments: string = ''): Boolean;
procedure CancelConsume(const aChannel, aConsumerTag: string; aNoWait: Boolean = false);
function CancelConsumeEx(const aChannel, aConsumerTag: string; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT): Boolean;
procedure PublishMessage(const aChannel, aExchange, aRoutingKey, aMessage: string; aMandatory: Boolean = false; aImmediate: Boolean = false);
procedure GetMessage(const aChannel, aQueue: string; aNoAck: Boolean = false);
function GetMessageEx(const aChannel, aQueue: string; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT): Boolean;
procedure AckMessage(const aChannel: string; aDeliveryTag: UInt64; aMultiple: Boolean = false);
procedure RejectMessage(const aChannel: string; aDeliveryTag: UInt64; aRequeue: Boolean = false);
procedure RecoverAsync(const aChannel: string; aRequeue: Boolean = false);
procedure Recover(const aChannel: string; aRequeue: Boolean = false);
function RecoverEx(const aChannel: string; aRequeue: Boolean = false; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT): Boolean;
procedure SelectTransaction(const aChannel: string);
function SelectTransactionEx(const aChannel: string; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT): Boolean;
procedure CommitTransaction(const aChannel: string);
function CommitTransactionEx(const aChannel: string; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT): Boolean;
procedure RollbackTransaction(const aChannel: string);
function RollbackTransactionEx(const aChannel: string; aTimeout: Integer = CS_AMQP_DEFAULT_TIMEOUT): Boolean;
procedure WriteData(const aText: String);
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Close(unsigned short aReplyCode, const UnicodeString aReplyText, TsgcAMQPClass * aFailClassId = amqpClassNone, TsgcAMQPMethod * aFailMethodId = amqpMethodNone);
bool __fastcall CloseEx(unsigned short aReplyCode, const UnicodeString aReplyText, TsgcAMQPClass * aFailClassId = amqpClassNone, TsgcAMQPMethod * aFailMethodId = amqpMethodNone);
void __fastcall OpenChannel(const UnicodeString aChannel);
bool __fastcall OpenChannelEx(const UnicodeString aChannel, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT);
void __fastcall CloseChannel(const UnicodeString aChannel, unsigned short aReplyCode = 0, const UnicodeString aReplyText = '', TsgcAMQPClass * aFailClassId = amqpClassNone, TsgcAMQPMethod * aFailMethodId = amqpMethodNone);
bool __fastcall CloseChannelEx(const UnicodeString aChannel, unsigned short aReplyCode = 0, const UnicodeString aReplyText = '', TsgcAMQPClass * aFailClassId = amqpClassNone, TsgcAMQPMethod * aFailMethodId = amqpMethodNone, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT);
void __fastcall EnableChannel(const UnicodeString aChannel);
bool __fastcall EnableChannelEx(const UnicodeString aChannel, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT);
void __fastcall DisableChannel(const UnicodeString aChannel);
bool __fastcall DisableChannelEx(const UnicodeString aChannel, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT);
void __fastcall DeclareExchange(const UnicodeString aChannel, const UnicodeString aExchange, const UnicodeString aExchangeType = 'direct', bool aPassive = false, bool aDurable = false, bool aAutoDelete = false, bool aInternal = false, bool aNoWait = false, const UnicodeString aArguments = '');
bool __fastcall DeclareExchangeEx(const UnicodeString aChannel, const UnicodeString aExchange, const UnicodeString aExchangeType = 'direct', bool aPassive = false, bool aDurable = false, bool aAutoDelete = false, bool aInternal = false, bool aNoWait = false, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT, const UnicodeString aArguments = '');
void __fastcall DeleteExchange(const UnicodeString aChannel, const UnicodeString aExchange, bool aIfUnused = false, bool aNoWait = false);
bool __fastcall DeleteExchangeEx(const UnicodeString aChannel, const UnicodeString aExchange, bool aIfUnused = false, bool aNoWait = false, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT);
void __fastcall DeclareQueue(const UnicodeString aChannel, const UnicodeString aQueue, bool aPassive = false, bool aDurable = false, bool aExclusive = false, bool aAutoDelete = false, bool aNoWait = false, const UnicodeString aArguments = '');
bool __fastcall DeclareQueueEx(const UnicodeString aChannel, const UnicodeString aQueue, bool aPassive = false, bool aDurable = false, bool aExclusive = false, bool aAutoDelete = false, bool aNoWait = false, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT, const UnicodeString aArguments = '');
void __fastcall BindQueue(const UnicodeString aChannel, const UnicodeString aQueue, const UnicodeString aExchange, const UnicodeString aRoutingKey, bool aNoWait = false, const UnicodeString aArguments = '');
bool __fastcall BindQueueEx(const UnicodeString aChannel, const UnicodeString aQueue, const UnicodeString aExchange, const UnicodeString aRoutingKey, bool aNoWait = false, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT, const UnicodeString aArguments = '');
void __fastcall UnBindQueue(const UnicodeString aChannel, const UnicodeString aQueue, const UnicodeString aExchange, const UnicodeString aRoutingKey, const UnicodeString aArguments = '');
bool __fastcall UnBindQueueEx(const UnicodeString aChannel, const UnicodeString aQueue, const UnicodeString aExchange, const UnicodeString aRoutingKey, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT, const UnicodeString aArguments = '');
void __fastcall PurgeQueue(const UnicodeString aChannel, const UnicodeString aQueue, bool aNoWait = false);
bool __fastcall PurgeQueueEx(const UnicodeString aChannel, const UnicodeString aQueue, bool aNoWait = false, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT);
void __fastcall DeleteQueue(const UnicodeString aChannel, const UnicodeString aQueue, bool aIfUnused = false, bool aIfEmpty = false, bool aNoWait = false);
bool __fastcall DeleteQueueEx(const UnicodeString aChannel, const UnicodeString aQueue, bool aIfUnused = false, bool aIfEmpty = false, bool aNoWait = false, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT);
void __fastcall SetQoS(const UnicodeString aChannel, unsigned int aPrefetchSize = 0, unsigned short aPrefetchCount = 0, bool aGlobal = false);
bool __fastcall SetQoSEx(const UnicodeString aChannel, unsigned int aPrefetchSize = 0, unsigned short aPrefetchCount = 0, bool aGlobal = false, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT);
void __fastcall Consume(const UnicodeString aChannel, const UnicodeString aQueue, const UnicodeString aConsumerTag = '', bool aNoLocal = false, bool aNoAck = false, bool aExclusive = false, bool aNoWait = false, const UnicodeString aArguments = '');
bool __fastcall ConsumeEx(const UnicodeString aChannel, const UnicodeString aQueue, const UnicodeString aConsumerTag = '', bool aNoLocal = false, bool aNoAck = false, bool aExclusive = false, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT, const UnicodeString aArguments = '');
void __fastcall CancelConsume(const UnicodeString aChannel, const UnicodeString aConsumerTag, bool aNoWait = false);
bool __fastcall CancelConsumeEx(const UnicodeString aChannel, const UnicodeString aConsumerTag, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT);
void __fastcall PublishMessage(const UnicodeString aChannel, const UnicodeString aExchange, const UnicodeString aRoutingKey, const UnicodeString aMessage, bool aMandatory = false, bool aImmediate = false);
void __fastcall GetMessage(const UnicodeString aChannel, const UnicodeString aQueue, bool aNoAck = false);
bool __fastcall GetMessageEx(const UnicodeString aChannel, const UnicodeString aQueue, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT);
void __fastcall AckMessage(const UnicodeString aChannel, unsigned long long aDeliveryTag, bool aMultiple = false);
void __fastcall RejectMessage(const UnicodeString aChannel, unsigned long long aDeliveryTag, bool aRequeue = false);
void __fastcall RecoverAsync(const UnicodeString aChannel, bool aRequeue = false);
void __fastcall Recover(const UnicodeString aChannel, bool aRequeue = false);
bool __fastcall RecoverEx(const UnicodeString aChannel, bool aRequeue = false, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT);
void __fastcall SelectTransaction(const UnicodeString aChannel);
bool __fastcall SelectTransactionEx(const UnicodeString aChannel, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT);
void __fastcall CommitTransaction(const UnicodeString aChannel);
bool __fastcall CommitTransactionEx(const UnicodeString aChannel, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT);
void __fastcall RollbackTransaction(const UnicodeString aChannel);
bool __fastcall RollbackTransactionEx(const UnicodeString aChannel, int aTimeout = CS_AMQP_DEFAULT_TIMEOUT);
void __fastcall WriteData(const UnicodeString aText);
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

