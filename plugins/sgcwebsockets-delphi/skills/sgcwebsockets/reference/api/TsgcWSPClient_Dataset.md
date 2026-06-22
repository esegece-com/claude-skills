# TsgcWSPClient_Dataset

unit: sgcWebSocket_Protocols
Edition: Professional and higher

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `DataSet: TDataSet` | `TDataSet` | `__property TDataSet * DataSet;` |
| `Broker: TsgcWSProtocol_Broker_Client` | [TsgcWSProtocol_Broker_Client](../types/TsgcWSProtocol_Broker_Client.md) | `__property TsgcWSProtocol_Broker_Client * Broker;` |
| `AutoEscapeText: Boolean` | `Boolean` | `__property bool AutoEscapeText;` |
| `EncodeBase64: Boolean` | `Boolean` | `__property bool EncodeBase64;` |
| `AutoSubscribe: Boolean` | `Boolean` | `__property bool AutoSubscribe;` |
| `NotifyUpdates: Boolean` | `Boolean` | `__property bool NotifyUpdates;` |
| `ApplyUpdates: Boolean` | `Boolean` | `__property bool ApplyUpdates;` |
| `UpdateMode: TwsDatasetUpdateMode` | [TwsDatasetUpdateMode](../types/TwsDatasetUpdateMode.md) | `__property TwsDatasetUpdateMode * UpdateMode;` |
| `QoS: TsgcWSQoS_Options` | [TsgcWSQoS_Options](../types/TsgcWSQoS_Options.md) | `__property TsgcWSQoS_Options * QoS;` |
| `FormatSettings: TsgcWSDatasetFormatSettings` | [TsgcWSDatasetFormatSettings](../types/TsgcWSDatasetFormatSettings.md) | `__property TsgcWSDatasetFormatSettings * FormatSettings;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `WSMessage: TsgcWSMessage` | [TsgcWSMessage](../types/TsgcWSMessage.md) | `__property TsgcWSMessage * WSMessage;` |
| `Subscriptions: TStringList` | `TStringList` | `__property TStringList * Subscriptions;` |
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
| `OnBeforeSynchronize: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnBeforeSynchronize;` |
| `OnAfterSynchronize: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAfterSynchronize;` |
| `OnMetaData: TsgcWSMetaDataEvent` | [TsgcWSMetaDataEvent](../types/TsgcWSMetaDataEvent.md) | `__property TsgcWSMetaDataEvent OnMetaData;` |
| `OnRPCResult: TsgcWSRPCResultEvent` | [TsgcWSRPCResultEvent](../types/TsgcWSRPCResultEvent.md) | `__property TsgcWSRPCResultEvent OnRPCResult;` |
| `OnRPCError: TsgcWSRPCErrorEvent` | [TsgcWSRPCErrorEvent](../types/TsgcWSRPCErrorEvent.md) | `__property TsgcWSRPCErrorEvent OnRPCError;` |
| `OnEvent: TsgcWSCustomEvent` | [TsgcWSCustomEvent](../types/TsgcWSCustomEvent.md) | `__property TsgcWSCustomEvent OnEvent;` |
| `OnAcknowledgment: TsgcWSAcknowledgment` | [TsgcWSAcknowledgment](../types/TsgcWSAcknowledgment.md) | `__property TsgcWSAcknowledgment * OnAcknowledgment;` |
| `OnSession: TsgcWSSessionEvent` | [TsgcWSSessionEvent](../types/TsgcWSSessionEvent.md) | `__property TsgcWSSessionEvent OnSession;` |

## Methods

Delphi

```pascal
procedure Subscribe_all;
procedure UnSubscribe_all;
procedure Synchronize;
procedure GetMetaData;
procedure WriteData(const aText: String);
procedure Subscribe(const aChannel: String; const aGuid: String = '');
procedure UnSubscribe(const aChannel: String; const aGuid: String = '');
procedure UnSubscribeAll(const aGuid: String = '');
procedure Broadcast(const aText: String; const aChannel: String = ''; const aGuid: String = '');
procedure RPC(const aId, aMethod: string; const aParams: string = ''; const aGuid: String = ''; const aQueue: TwsQueue = queueLevel0);
procedure Notify(const aMethod: string; const aParams: string = ''; const aGuid: String = ''; const aQueue: TwsQueue = queueLevel0);
procedure Publish(const aText, aChannel: String; const aGuid: String = ''; const aQueue: TwsQueue = queueLevel0);
procedure GetSession;
procedure StartTransaction(const aChannel: string = '');
procedure Commit(const aChannel: string = '');
procedure RollBack(const aChannel: string = '');
function GetRPCMethodById(const aId: String): string;
function GetRPCParamsById(const aId: String): string;
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Subscribe_all();
void __fastcall UnSubscribe_all();
void __fastcall Synchronize();
void __fastcall GetMetaData();
void __fastcall WriteData(const UnicodeString aText);
void __fastcall Subscribe(const UnicodeString aChannel, const UnicodeString aGuid = '');
void __fastcall UnSubscribe(const UnicodeString aChannel, const UnicodeString aGuid = '');
void __fastcall UnSubscribeAll(const UnicodeString aGuid = '');
void __fastcall Broadcast(const UnicodeString aText, const UnicodeString aChannel = '', const UnicodeString aGuid = '');
void __fastcall RPC(const UnicodeString aId, const UnicodeString aMethod, const UnicodeString aParams = '', const UnicodeString aGuid = '', const TwsQueue * aQueue = queueLevel0);
void __fastcall Notify(const UnicodeString aMethod, const UnicodeString aParams = '', const UnicodeString aGuid = '', const TwsQueue * aQueue = queueLevel0);
void __fastcall Publish(const UnicodeString aText, const UnicodeString aChannel, const UnicodeString aGuid = '', const TwsQueue * aQueue = queueLevel0);
void __fastcall GetSession();
void __fastcall StartTransaction(const UnicodeString aChannel = '');
void __fastcall Commit(const UnicodeString aChannel = '');
void __fastcall RollBack(const UnicodeString aChannel = '');
UnicodeString __fastcall GetRPCMethodById(const UnicodeString aId);
UnicodeString __fastcall GetRPCParamsById(const UnicodeString aId);
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

