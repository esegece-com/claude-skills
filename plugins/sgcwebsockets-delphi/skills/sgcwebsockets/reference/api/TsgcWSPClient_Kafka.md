# TsgcWSPClient_Kafka

unit: sgcWebSocket_Protocols
Edition: requires SGC_KAFKA

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `KafkaOptions: TsgcKafka_Options` | [TsgcKafka_Options](../types/TsgcKafka_Options.md) | `__property TsgcKafka_Options * KafkaOptions;` |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `Broker: TsgcWSProtocol_Broker_Client` | [TsgcWSProtocol_Broker_Client](../types/TsgcWSProtocol_Broker_Client.md) | `__property TsgcWSProtocol_Broker_Client * Broker;` |
| `Protocol: string (read-only)` | `string` | `__property UnicodeString Protocol /* read-only */;` |
| `MsgType: TwsProtocolMessage` | [TwsProtocolMessage](../types/TwsProtocolMessage.md) | `__property TwsProtocolMessage * MsgType;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnKafkaConnect: TsgcKafkaConnectEvent` | [TsgcKafkaConnectEvent](../types/TsgcKafkaConnectEvent.md) | `__property TsgcKafkaConnectEvent OnKafkaConnect;` |
| `OnKafkaDisconnect: TsgcKafkaDisconnectEvent` | [TsgcKafkaDisconnectEvent](../types/TsgcKafkaDisconnectEvent.md) | `__property TsgcKafkaDisconnectEvent OnKafkaDisconnect;` |
| `OnKafkaMessage: TsgcKafkaMessageEvent` | [TsgcKafkaMessageEvent](../types/TsgcKafkaMessageEvent.md) | `__property TsgcKafkaMessageEvent OnKafkaMessage;` |
| `OnKafkaError: TsgcKafkaErrorEvent` | [TsgcKafkaErrorEvent](../types/TsgcKafkaErrorEvent.md) | `__property TsgcKafkaErrorEvent OnKafkaError;` |
| `OnKafkaRebalance: TsgcKafkaRebalanceEvent` | [TsgcKafkaRebalanceEvent](../types/TsgcKafkaRebalanceEvent.md) | `__property TsgcKafkaRebalanceEvent OnKafkaRebalance;` |
| `OnKafkaProduce: TsgcKafkaProduceEvent` | [TsgcKafkaProduceEvent](../types/TsgcKafkaProduceEvent.md) | `__property TsgcKafkaProduceEvent OnKafkaProduce;` |
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
procedure Produce(const aTopic: string; const aValue: string; const aKey: string = ''; aPartition: Integer = -1);
procedure ProduceBytes(const aTopic: string; const aValue: TBytes; const aKey: TBytes; aPartition: Integer = -1);
function ProduceMessages(const aTopic: string; aPartition: Integer; const aMessages: TsgcKafkaMessages): TsgcKafkaProduceResponse;
procedure Subscribe(const aTopics: array of string);
procedure Unsubscribe;
function Poll(aTimeoutMs: Integer = 1000): TsgcKafkaMessages;
procedure CommitSync;
procedure CommitOffset(const aTopic: string; aPartition: Integer; aOffset: Int64);
function FetchMessages(const aTopic: string; aPartition: Integer; aOffset: Int64; aMaxBytes: Integer = 0): TsgcKafkaMessages;
function GetCommittedOffset(const aTopic: string; aPartition: Integer): Int64;
function GetLatestOffset(const aTopic: string; aPartition: Integer): Int64;
function GetEarliestOffset(const aTopic: string; aPartition: Integer): Int64;
procedure CreateTopic(const aTopicName: string; aNumPartitions: Integer = 1; aReplicationFactor: Integer = 1);
procedure DeleteTopic(const aTopicName: string);
function GetMetadata(const aTopics: array of string) : TsgcKafkaMetadataResponse;
function ListGroups: TsgcKafkaListGroupsResponse;
function DescribeGroups(const aGroupIds: array of string) : TsgcKafkaDescribeGroupsResponse;
function GetApiVersions: TsgcKafkaApiVersionsResponse;
procedure DoKafkaConnectEvent;
procedure DoKafkaDisconnectEvent(aCode: Integer);
procedure DoKafkaMessageEvent(const aMessage: TsgcKafkaMessage);
procedure DoKafkaErrorEvent(const aErrorCode: Integer; const aErrorMessage: string);
procedure DoKafkaRebalanceEvent(const aGroupId, aMemberId: string; aGenerationId: Integer);
procedure DoKafkaProduceEvent(const aTopic: string; aPartition: Integer; aOffset: Int64; aErrorCode: SmallInt);
procedure WriteData(const aText: String);
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Produce(const UnicodeString aTopic, const UnicodeString aValue, const UnicodeString aKey = '', int aPartition = -1);
void __fastcall ProduceBytes(const UnicodeString aTopic, const System::DynamicArray<System::Byte> aValue, const System::DynamicArray<System::Byte> aKey, int aPartition = -1);
TsgcKafkaProduceResponse * __fastcall ProduceMessages(const UnicodeString aTopic, int aPartition, const TsgcKafkaMessages * aMessages);
void __fastcall Subscribe(const array of string aTopics);
void __fastcall Unsubscribe();
TsgcKafkaMessages * __fastcall Poll(int aTimeoutMs = 1000);
void __fastcall CommitSync();
void __fastcall CommitOffset(const UnicodeString aTopic, int aPartition, long long aOffset);
TsgcKafkaMessages * __fastcall FetchMessages(const UnicodeString aTopic, int aPartition, long long aOffset, int aMaxBytes = 0);
long long __fastcall GetCommittedOffset(const UnicodeString aTopic, int aPartition);
long long __fastcall GetLatestOffset(const UnicodeString aTopic, int aPartition);
long long __fastcall GetEarliestOffset(const UnicodeString aTopic, int aPartition);
void __fastcall CreateTopic(const UnicodeString aTopicName, int aNumPartitions = 1, int aReplicationFactor = 1);
void __fastcall DeleteTopic(const UnicodeString aTopicName);
TsgcKafkaMetadataResponse * __fastcall GetMetadata(const array of string aTopics);
TsgcKafkaListGroupsResponse * __fastcall ListGroups();
TsgcKafkaDescribeGroupsResponse * __fastcall DescribeGroups(const array of string aGroupIds);
TsgcKafkaApiVersionsResponse * __fastcall GetApiVersions();
void __fastcall DoKafkaConnectEvent();
void __fastcall DoKafkaDisconnectEvent(int aCode);
void __fastcall DoKafkaMessageEvent(const TsgcKafkaMessage * aMessage);
void __fastcall DoKafkaErrorEvent(const int aErrorCode, const UnicodeString aErrorMessage);
void __fastcall DoKafkaRebalanceEvent(const UnicodeString aGroupId, const UnicodeString aMemberId, int aGenerationId);
void __fastcall DoKafkaProduceEvent(const UnicodeString aTopic, int aPartition, long long aOffset, short aErrorCode);
void __fastcall WriteData(const UnicodeString aText);
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

