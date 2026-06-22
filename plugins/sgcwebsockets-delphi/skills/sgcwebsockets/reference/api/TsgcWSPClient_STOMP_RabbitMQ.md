# TsgcWSPClient_STOMP_RabbitMQ

unit: sgcWebSocket_Protocols
Edition: Standard

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcHTTP_API_Pinecone` | [TsgcHTTP_API_Pinecone](../types/TsgcHTTP_API_Pinecone.md) | `__property TsgcHTTP_API_Pinecone * Client;` |
| `Broker: TsgcWSProtocol_Broker_Client` | [TsgcWSProtocol_Broker_Client](../types/TsgcWSProtocol_Broker_Client.md) | `__property TsgcWSProtocol_Broker_Client * Broker;` |
| `Authentication: TsgcAMQP1AuthenticationType` | [TsgcAMQP1AuthenticationType](../types/TsgcAMQP1AuthenticationType.md) | `__property TsgcAMQP1AuthenticationType * Authentication;` |
| `HeartBeat: TsgcAI_MCP_Client_HeartBeatOptions` | [TsgcAI_MCP_Client_HeartBeatOptions](../types/TsgcAI_MCP_Client_HeartBeatOptions.md) | `__property TsgcAI_MCP_Client_HeartBeatOptions * HeartBeat;` |
| `Versions: TsgcWSSTOMPVersion_Options` | [TsgcWSSTOMPVersion_Options](../types/TsgcWSSTOMPVersion_Options.md) | `__property TsgcWSSTOMPVersion_Options * Versions;` |
| `Options: TsgcHTMLChat_Options` | [TsgcHTMLChat_Options](../types/TsgcHTMLChat_Options.md) | `__property TsgcHTMLChat_Options * Options;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: string` | `string` | `__property UnicodeString Version;` |
| `Queue: TsgcWSRabbitMQSTOMP_Queue_Options` | [TsgcWSRabbitMQSTOMP_Queue_Options](../types/TsgcWSRabbitMQSTOMP_Queue_Options.md) | `__property TsgcWSRabbitMQSTOMP_Queue_Options * Queue;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnRabbitMQConnected: TsgcWSRabbitMQSTOMPConnectedEvent` | [TsgcWSRabbitMQSTOMPConnectedEvent](../types/TsgcWSRabbitMQSTOMPConnectedEvent.md) | `__property TsgcWSRabbitMQSTOMPConnectedEvent OnRabbitMQConnected;` |
| `OnRabbitMQMessage: TsgcWSRabbitMQSTOMPMessageEvent` | [TsgcWSRabbitMQSTOMPMessageEvent](../types/TsgcWSRabbitMQSTOMPMessageEvent.md) | `__property TsgcWSRabbitMQSTOMPMessageEvent OnRabbitMQMessage;` |
| `OnRabbitMQReceipt: TsgcWSRabbitMQSTOMPReceiptEvent` | [TsgcWSRabbitMQSTOMPReceiptEvent](../types/TsgcWSRabbitMQSTOMPReceiptEvent.md) | `__property TsgcWSRabbitMQSTOMPReceiptEvent OnRabbitMQReceipt;` |
| `OnRabbitMQError: TsgcWSRabbitMQSTOMPErrorEvent` | [TsgcWSRabbitMQSTOMPErrorEvent](../types/TsgcWSRabbitMQSTOMPErrorEvent.md) | `__property TsgcWSRabbitMQSTOMPErrorEvent OnRabbitMQError;` |
| `OnRabbitMQDisconnected: TsgcWSRabbitMQDisconnectedEvent` | [TsgcWSRabbitMQDisconnectedEvent](../types/TsgcWSRabbitMQDisconnectedEvent.md) | `__property TsgcWSRabbitMQDisconnectedEvent OnRabbitMQDisconnected;` |
| `OnRabbitMQPing: TsgcWSRabbitMQPingEvent` | [TsgcWSRabbitMQPingEvent](../types/TsgcWSRabbitMQPingEvent.md) | `__property TsgcWSRabbitMQPingEvent OnRabbitMQPing;` |

## Methods

Delphi

```pascal
procedure SubscribeEx(const aDestination: String; const aDurable: Boolean = True; const aAutoDelete: Boolean = False; const aExclusive: Boolean = False; const aACK: TsgcSTOMPACK = ackAuto; const aOptions: TsgcWSRabbitMQSTOMP_Queue_Options = nil);
procedure PublishEx(const aDestination, aText: String; const aContentType: String = CS_TEXT_PLAIN; const aTransaction: String = ''; const aHeaders: TStrings = nil);
procedure UnSubscribeEx(const aDestination: String);
procedure SubscribeTopic(const aTopic: String; const aDurable: Boolean = True; const aAutoDelete: Boolean = False; const aExclusive: Boolean = False; const aACK: TsgcSTOMPACK = ackAuto; const aOptions: TsgcWSRabbitMQSTOMP_Queue_Options = nil);
procedure UnSubscribeTopic(const aTopic: String);
procedure PublishTopic(const aTopic, aText: String; const aContentType: String = CS_TEXT_PLAIN; const aTransaction: String = ''; const aHeaders: TStrings = nil);
procedure SubscribeQueue(const aQueue: String; const aDurable: Boolean = True; const aAutoDelete: Boolean = False; const aExclusive: Boolean = False; const aACK: TsgcSTOMPACK = ackAuto; const aOptions: TsgcWSRabbitMQSTOMP_Queue_Options = nil);
procedure UnSubscribeQueue(const aQueue: String);
procedure PublishQueue(const aQueue, aText: String; const aContentType: String = CS_TEXT_PLAIN; const aTransaction: String = ''; const aHeaders: TStrings = nil);
procedure SubscribeQueueOutside(const aQueue: String; const aDurable: Boolean = True; const aAutoDelete: Boolean = False; const aExclusive: Boolean = False; const aACK: TsgcSTOMPACK = ackAuto; const aOptions: TsgcWSRabbitMQSTOMP_Queue_Options = nil);
procedure UnSubscribeQueueOutside(const aQueue: String);
procedure PublishQueueOutside(const aQueue, aText: String; const aContentType: String = CS_TEXT_PLAIN; const aTransaction: String = ''; const aHeaders: TStrings = nil);
procedure SubscribeTemporaryQueue(const aQueue, aReplyTo: String; const aDurable: Boolean = True; const aAutoDelete: Boolean = False; const aExclusive: Boolean = False; const aACK: TsgcSTOMPACK = ackAuto; const aOptions: TsgcWSRabbitMQSTOMP_Queue_Options = nil);
procedure UnSubscribeTemporaryQueue(const aQueue: String);
procedure PublishTemporaryQueue(const aQueue, aReplyTo, aText: String; const aContentType: String = CS_TEXT_PLAIN; const aTransaction: String = ''; const aHeaders: TStrings = nil);
procedure SubscribeExchange(const aName, aPattern: String; const aDurable: Boolean = True; const aAutoDelete: Boolean = False; const aExclusive: Boolean = False; const aACK: TsgcSTOMPACK = ackAuto; const aOptions: TsgcWSRabbitMQSTOMP_Queue_Options = nil);
procedure UnSubscribeExchange(const aName, aPattern: String);
procedure PublishExchange(const aName, aRoutingKey, aText: String; const aContentType: String = CS_TEXT_PLAIN; const aTransaction: String = ''; const aHeaders: TStrings = nil);
```

C++Builder

```cpp
void __fastcall SubscribeEx(const UnicodeString aDestination, const bool aDurable = True, const bool aAutoDelete = False, const bool aExclusive = False, const TsgcSTOMPACK * aACK = ackAuto, const TsgcWSRabbitMQSTOMP_Queue_Options * aOptions = nil);
void __fastcall PublishEx(const UnicodeString aDestination, const UnicodeString aText, const UnicodeString aContentType = CS_TEXT_PLAIN, const UnicodeString aTransaction = '', const TStrings * aHeaders = nil);
void __fastcall UnSubscribeEx(const UnicodeString aDestination);
void __fastcall SubscribeTopic(const UnicodeString aTopic, const bool aDurable = True, const bool aAutoDelete = False, const bool aExclusive = False, const TsgcSTOMPACK * aACK = ackAuto, const TsgcWSRabbitMQSTOMP_Queue_Options * aOptions = nil);
void __fastcall UnSubscribeTopic(const UnicodeString aTopic);
void __fastcall PublishTopic(const UnicodeString aTopic, const UnicodeString aText, const UnicodeString aContentType = CS_TEXT_PLAIN, const UnicodeString aTransaction = '', const TStrings * aHeaders = nil);
void __fastcall SubscribeQueue(const UnicodeString aQueue, const bool aDurable = True, const bool aAutoDelete = False, const bool aExclusive = False, const TsgcSTOMPACK * aACK = ackAuto, const TsgcWSRabbitMQSTOMP_Queue_Options * aOptions = nil);
void __fastcall UnSubscribeQueue(const UnicodeString aQueue);
void __fastcall PublishQueue(const UnicodeString aQueue, const UnicodeString aText, const UnicodeString aContentType = CS_TEXT_PLAIN, const UnicodeString aTransaction = '', const TStrings * aHeaders = nil);
void __fastcall SubscribeQueueOutside(const UnicodeString aQueue, const bool aDurable = True, const bool aAutoDelete = False, const bool aExclusive = False, const TsgcSTOMPACK * aACK = ackAuto, const TsgcWSRabbitMQSTOMP_Queue_Options * aOptions = nil);
void __fastcall UnSubscribeQueueOutside(const UnicodeString aQueue);
void __fastcall PublishQueueOutside(const UnicodeString aQueue, const UnicodeString aText, const UnicodeString aContentType = CS_TEXT_PLAIN, const UnicodeString aTransaction = '', const TStrings * aHeaders = nil);
void __fastcall SubscribeTemporaryQueue(const UnicodeString aQueue, const UnicodeString aReplyTo, const bool aDurable = True, const bool aAutoDelete = False, const bool aExclusive = False, const TsgcSTOMPACK * aACK = ackAuto, const TsgcWSRabbitMQSTOMP_Queue_Options * aOptions = nil);
void __fastcall UnSubscribeTemporaryQueue(const UnicodeString aQueue);
void __fastcall PublishTemporaryQueue(const UnicodeString aQueue, const UnicodeString aReplyTo, const UnicodeString aText, const UnicodeString aContentType = CS_TEXT_PLAIN, const UnicodeString aTransaction = '', const TStrings * aHeaders = nil);
void __fastcall SubscribeExchange(const UnicodeString aName, const UnicodeString aPattern, const bool aDurable = True, const bool aAutoDelete = False, const bool aExclusive = False, const TsgcSTOMPACK * aACK = ackAuto, const TsgcWSRabbitMQSTOMP_Queue_Options * aOptions = nil);
void __fastcall UnSubscribeExchange(const UnicodeString aName, const UnicodeString aPattern);
void __fastcall PublishExchange(const UnicodeString aName, const UnicodeString aRoutingKey, const UnicodeString aText, const UnicodeString aContentType = CS_TEXT_PLAIN, const UnicodeString aTransaction = '', const TStrings * aHeaders = nil);
```

