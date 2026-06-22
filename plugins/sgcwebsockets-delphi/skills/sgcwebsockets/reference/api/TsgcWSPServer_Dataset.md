# TsgcWSPServer_Dataset

unit: sgcWebSocket_Protocols
Edition: Professional and higher

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Server: TsgcWSComponent_Server` | [TsgcWSComponent_Server](../types/TsgcWSComponent_Server.md) | `__property TsgcWSComponent_Server * Server;` |
| `DataSet: TDataSet` | `TDataSet` | `__property TDataSet * DataSet;` |
| `Broker: TsgcWSProtocol_Broker_Server` | [TsgcWSProtocol_Broker_Server](../types/TsgcWSProtocol_Broker_Server.md) | `__property TsgcWSProtocol_Broker_Server * Broker;` |
| `RPCAuthentication: TsgcWSAuthentication_Methods` | [TsgcWSAuthentication_Methods](../types/TsgcWSAuthentication_Methods.md) | `__property TsgcWSAuthentication_Methods * RPCAuthentication;` |
| `AutoEscapeText: Boolean` | `Boolean` | `__property bool AutoEscapeText;` |
| `EncodeBase64: Boolean` | `Boolean` | `__property bool EncodeBase64;` |
| `AutoSynchronize: Boolean` | `Boolean` | `__property bool AutoSynchronize;` |
| `NotifyUpdates: Boolean` | `Boolean` | `__property bool NotifyUpdates;` |
| `ApplyUpdates: Boolean` | `Boolean` | `__property bool ApplyUpdates;` |
| `UpdateMode: TwsDatasetUpdateMode` | [TwsDatasetUpdateMode](../types/TwsDatasetUpdateMode.md) | `__property TwsDatasetUpdateMode * UpdateMode;` |
| `FormatSettings: TsgcWSDatasetFormatSettings` | [TsgcWSDatasetFormatSettings](../types/TsgcWSDatasetFormatSettings.md) | `__property TsgcWSDatasetFormatSettings * FormatSettings;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `NotifyDeletes: Boolean` | `Boolean` | `__property bool NotifyDeletes;` |
| `QoS: TsgcWSQoS_Options` | [TsgcWSQoS_Options](../types/TsgcWSQoS_Options.md) | `__property TsgcWSQoS_Options * QoS;` |
| `Subscriptions: TsgcQueueListChannels` | [TsgcQueueListChannels](../types/TsgcQueueListChannels.md) | `__property TsgcQueueListChannels * Subscriptions;` |
| `UseMatchesMask: Boolean` | `Boolean` | `__property bool UseMatchesMask;` |
| `Protocol: string (read-only)` | `string` | `__property UnicodeString Protocol /* read-only */;` |
| `MsgType: TwsProtocolMessage` | [TwsProtocolMessage](../types/TwsProtocolMessage.md) | `__property TwsProtocolMessage * MsgType;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnBeforeSubscription: TsgcWSBeforeSubscriptionEvent` | [TsgcWSBeforeSubscriptionEvent](../types/TsgcWSBeforeSubscriptionEvent.md) | `__property TsgcWSBeforeSubscriptionEvent OnBeforeSubscription;` |
| `OnSubscription: TsgcWSSubscriptionEvent` | [TsgcWSSubscriptionEvent](../types/TsgcWSSubscriptionEvent.md) | `__property TsgcWSSubscriptionEvent OnSubscription;` |
| `OnUnSubscription: TsgcWSSubscriptionEvent` | [TsgcWSSubscriptionEvent](../types/TsgcWSSubscriptionEvent.md) | `__property TsgcWSSubscriptionEvent OnUnSubscription;` |
| `OnRawMessage: TsgcOnWhatsAppServerMessage` | [TsgcOnWhatsAppServerMessage](../types/TsgcOnWhatsAppServerMessage.md) | `__property TsgcOnWhatsAppServerMessage * OnRawMessage;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |
| `OnBeforeNewRecord: TsgcWSBeforeRecordEvent` | [TsgcWSBeforeRecordEvent](../types/TsgcWSBeforeRecordEvent.md) | `__property TsgcWSBeforeRecordEvent OnBeforeNewRecord;` |
| `OnBeforeUpdateRecord: TsgcWSBeforeRecordEvent` | [TsgcWSBeforeRecordEvent](../types/TsgcWSBeforeRecordEvent.md) | `__property TsgcWSBeforeRecordEvent OnBeforeUpdateRecord;` |
| `OnBeforeDeleteRecord: TsgcWSBeforeRecordEvent` | [TsgcWSBeforeRecordEvent](../types/TsgcWSBeforeRecordEvent.md) | `__property TsgcWSBeforeRecordEvent OnBeforeDeleteRecord;` |
| `OnAfterNewRecord: TsgcWSAfterRecordEvent` | [TsgcWSAfterRecordEvent](../types/TsgcWSAfterRecordEvent.md) | `__property TsgcWSAfterRecordEvent OnAfterNewRecord;` |
| `OnAfterUpdateRecord: TsgcWSAfterRecordEvent` | [TsgcWSAfterRecordEvent](../types/TsgcWSAfterRecordEvent.md) | `__property TsgcWSAfterRecordEvent OnAfterUpdateRecord;` |
| `OnAfterDeleteRecord: TsgcWSAfterRecordEvent` | [TsgcWSAfterRecordEvent](../types/TsgcWSAfterRecordEvent.md) | `__property TsgcWSAfterRecordEvent OnAfterDeleteRecord;` |
| `OnBeforeDatasetUpdate: TsgcWSBeforeDatasetUpdateEvent` | [TsgcWSBeforeDatasetUpdateEvent](../types/TsgcWSBeforeDatasetUpdateEvent.md) | `__property TsgcWSBeforeDatasetUpdateEvent OnBeforeDatasetUpdate;` |
| `OnNotification: TsgcWSNotificationEvent` | [TsgcWSNotificationEvent](../types/TsgcWSNotificationEvent.md) | `__property TsgcWSNotificationEvent OnNotification;` |
| `OnRPC: TsgcWSRPCEvent` | [TsgcWSRPCEvent](../types/TsgcWSRPCEvent.md) | `__property TsgcWSRPCEvent OnRPC;` |
| `OnRPCAuthentication: TsgcWSRPCAuthenticationEvent` | [TsgcWSRPCAuthenticationEvent](../types/TsgcWSRPCAuthenticationEvent.md) | `__property TsgcWSRPCAuthenticationEvent OnRPCAuthentication;` |
| `OnBeforePublish: TsgcWSBeforePublish` | [TsgcWSBeforePublish](../types/TsgcWSBeforePublish.md) | `__property TsgcWSBeforePublish * OnBeforePublish;` |
| `OnAcknowledgment: TsgcWSAcknowledgment` | [TsgcWSAcknowledgment](../types/TsgcWSAcknowledgment.md) | `__property TsgcWSAcknowledgment * OnAcknowledgment;` |

## Methods

Delphi

```pascal
procedure MetaData(aConnection: TsgcWSConnection);
procedure Synchronize(aConnection: TsgcWSConnection);
procedure BroadcastRecord;
function WriteData(aGuid, aMessage: string): Boolean;
procedure Broadcast(aMessage: string; aChannel: string = ''; Exclude: String = ''; Include: String = '');
function ClearQueue(const aChannel: String): Boolean;
procedure Publish(const aMessage, aChannel: String; const aExclude: String = ''; const aInclude: String = ''; const aQueue: TwsQueue = queueLevel0);
procedure RPCResult(aID, aResult: String);
procedure RPCError(aID: String; aCode: Integer; aMessage: String; aData: String = '');
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall MetaData(TsgcWSConnection * aConnection);
void __fastcall Synchronize(TsgcWSConnection * aConnection);
void __fastcall BroadcastRecord();
bool __fastcall WriteData(UnicodeString aGuid, UnicodeString aMessage);
void __fastcall Broadcast(UnicodeString aMessage, UnicodeString aChannel = '', UnicodeString Exclude = '', UnicodeString Include = '');
bool __fastcall ClearQueue(const UnicodeString aChannel);
void __fastcall Publish(const UnicodeString aMessage, const UnicodeString aChannel, const UnicodeString aExclude = '', const UnicodeString aInclude = '', const TwsQueue * aQueue = queueLevel0);
void __fastcall RPCResult(UnicodeString aID, UnicodeString aResult);
void __fastcall RPCError(UnicodeString aID, int aCode, UnicodeString aMessage, UnicodeString aData = '');
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

