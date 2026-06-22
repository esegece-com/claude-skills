# TsgcWSPClient_STOMP_ActiveMQ

unit: sgcWebSocket_Protocols

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
| `ActiveMQ_Options: TsgcWSActiveMQSTOMP_Options` | [TsgcWSActiveMQSTOMP_Options](../types/TsgcWSActiveMQSTOMP_Options.md) | `__property TsgcWSActiveMQSTOMP_Options * ActiveMQ_Options;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: string` | `string` | `__property UnicodeString Version;` |
| `Queue: TsgcWSActiveMQSTOMP_Queue_Options` | [TsgcWSActiveMQSTOMP_Queue_Options](../types/TsgcWSActiveMQSTOMP_Queue_Options.md) | `__property TsgcWSActiveMQSTOMP_Queue_Options * Queue;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnActiveMQConnected: TsgcWSActiveMQSTOMPConnectedEvent` | [TsgcWSActiveMQSTOMPConnectedEvent](../types/TsgcWSActiveMQSTOMPConnectedEvent.md) | `__property TsgcWSActiveMQSTOMPConnectedEvent OnActiveMQConnected;` |
| `OnActiveMQMessage: TsgcWSActiveMQSTOMPMessageEvent` | [TsgcWSActiveMQSTOMPMessageEvent](../types/TsgcWSActiveMQSTOMPMessageEvent.md) | `__property TsgcWSActiveMQSTOMPMessageEvent OnActiveMQMessage;` |
| `OnActiveMQReceipt: TsgcWSActiveMQSTOMPReceiptEvent` | [TsgcWSActiveMQSTOMPReceiptEvent](../types/TsgcWSActiveMQSTOMPReceiptEvent.md) | `__property TsgcWSActiveMQSTOMPReceiptEvent OnActiveMQReceipt;` |
| `OnActiveMQError: TsgcWSActiveMQSTOMPErrorEvent` | [TsgcWSActiveMQSTOMPErrorEvent](../types/TsgcWSActiveMQSTOMPErrorEvent.md) | `__property TsgcWSActiveMQSTOMPErrorEvent OnActiveMQError;` |
| `OnActiveMQDisconnected: TsgcWSActiveMQDisconnectedEvent` | [TsgcWSActiveMQDisconnectedEvent](../types/TsgcWSActiveMQDisconnectedEvent.md) | `__property TsgcWSActiveMQDisconnectedEvent OnActiveMQDisconnected;` |
| `OnActiveMQPing: TsgcWSActiveMQPingEvent` | [TsgcWSActiveMQPingEvent](../types/TsgcWSActiveMQPingEvent.md) | `__property TsgcWSActiveMQPingEvent OnActiveMQPing;` |

## Methods

Delphi

```pascal
procedure SubscribeEx(const aDestination: String; const aDurable: Boolean = True; const aExclusive: Boolean = False; const aACK: TsgcSTOMPACK = ackAuto; const aOptions: TsgcWSActiveMQSTOMP_Queue_Options = nil);
procedure PublishEx(const aDestination, aText: String; const aContentType: String = CS_TEXT_PLAIN; const aTransaction: String = ''; const aOptions: TsgcWSActiveMQSTOMP_Message_Options = nil);
procedure UnSubscribeEx(const aDestination: String);
procedure SubscribeTopic(const aTopic: String; const aDurable: Boolean = True; const aExclusive: Boolean = False; const aACK: TsgcSTOMPACK = ackAuto; const aOptions: TsgcWSActiveMQSTOMP_Queue_Options = nil);
procedure UnSubscribeTopic(const aTopic: String);
procedure PublishTopic(const aTopic, aText: String; const aContentType: String = CS_TEXT_PLAIN; const aTransaction: String = ''; const aOptions: TsgcWSActiveMQSTOMP_Message_Options = nil);
procedure SubscribeQueue(const aQueue: String; const aDurable: Boolean = True; const aExclusive: Boolean = False; const aACK: TsgcSTOMPACK = ackAuto; const aOptions: TsgcWSActiveMQSTOMP_Queue_Options = nil);
procedure UnSubscribeQueue(const aQueue: String);
procedure PublishQueue(const aQueue, aText: String; const aContentType: String = CS_TEXT_PLAIN; const aTransaction: String = ''; const aOptions: TsgcWSActiveMQSTOMP_Message_Options = nil);
```

C++Builder

```cpp
void __fastcall SubscribeEx(const UnicodeString aDestination, const bool aDurable = True, const bool aExclusive = False, const TsgcSTOMPACK * aACK = ackAuto, const TsgcWSActiveMQSTOMP_Queue_Options * aOptions = nil);
void __fastcall PublishEx(const UnicodeString aDestination, const UnicodeString aText, const UnicodeString aContentType = CS_TEXT_PLAIN, const UnicodeString aTransaction = '', const TsgcWSActiveMQSTOMP_Message_Options * aOptions = nil);
void __fastcall UnSubscribeEx(const UnicodeString aDestination);
void __fastcall SubscribeTopic(const UnicodeString aTopic, const bool aDurable = True, const bool aExclusive = False, const TsgcSTOMPACK * aACK = ackAuto, const TsgcWSActiveMQSTOMP_Queue_Options * aOptions = nil);
void __fastcall UnSubscribeTopic(const UnicodeString aTopic);
void __fastcall PublishTopic(const UnicodeString aTopic, const UnicodeString aText, const UnicodeString aContentType = CS_TEXT_PLAIN, const UnicodeString aTransaction = '', const TsgcWSActiveMQSTOMP_Message_Options * aOptions = nil);
void __fastcall SubscribeQueue(const UnicodeString aQueue, const bool aDurable = True, const bool aExclusive = False, const TsgcSTOMPACK * aACK = ackAuto, const TsgcWSActiveMQSTOMP_Queue_Options * aOptions = nil);
void __fastcall UnSubscribeQueue(const UnicodeString aQueue);
void __fastcall PublishQueue(const UnicodeString aQueue, const UnicodeString aText, const UnicodeString aContentType = CS_TEXT_PLAIN, const UnicodeString aTransaction = '', const TsgcWSActiveMQSTOMP_Message_Options * aOptions = nil);
```

