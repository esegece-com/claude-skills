# TsgcWSPClient_E2EE

unit: sgcWebSocket_Protocols
Edition: Enterprise

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `E2EE_Options: TsgcE2EE_Client_Options` | [TsgcE2EE_Client_Options](../types/TsgcE2EE_Client_Options.md) | `__property TsgcE2EE_Client_Options * E2EE_Options;` |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Broker: TsgcWSProtocol_Broker_Client` | [TsgcWSProtocol_Broker_Client](../types/TsgcWSProtocol_Broker_Client.md) | `__property TsgcWSProtocol_Broker_Client * Broker;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `Subscriptions: TStringList` | `TStringList` | `__property TStringList * Subscriptions;` |
| `Protocol: string (read-only)` | `string` | `__property UnicodeString Protocol /* read-only */;` |
| `MsgType: TwsProtocolMessage` | [TwsProtocolMessage](../types/TwsProtocolMessage.md) | `__property TwsProtocolMessage * MsgType;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnE2EEError: TsgcWSE2EEOnErrorEvent` | [TsgcWSE2EEOnErrorEvent](../types/TsgcWSE2EEOnErrorEvent.md) | `__property TsgcWSE2EEOnErrorEvent OnE2EEError;` |
| `OnE2EEMessageText: TsgcWSE2EEOnMessageText` | [TsgcWSE2EEOnMessageText](../types/TsgcWSE2EEOnMessageText.md) | `__property TsgcWSE2EEOnMessageText * OnE2EEMessageText;` |
| `OnE2EEMessageBinary: TsgcWSE2EEOnMessageBinary` | [TsgcWSE2EEOnMessageBinary](../types/TsgcWSE2EEOnMessageBinary.md) | `__property TsgcWSE2EEOnMessageBinary * OnE2EEMessageBinary;` |
| `OnE2EEMessageAck: TsgcWSE2EEOnMessageAckEvent` | [TsgcWSE2EEOnMessageAckEvent](../types/TsgcWSE2EEOnMessageAckEvent.md) | `__property TsgcWSE2EEOnMessageAckEvent OnE2EEMessageAck;` |
| `OnE2EEUserCreated: TsgcWSE2EEClientOnUserCreated` | [TsgcWSE2EEClientOnUserCreated](../types/TsgcWSE2EEClientOnUserCreated.md) | `__property TsgcWSE2EEClientOnUserCreated * OnE2EEUserCreated;` |
| `OnE2EEUserDeleted: TsgcWSE2EEClientOnUserDeleted` | [TsgcWSE2EEClientOnUserDeleted](../types/TsgcWSE2EEClientOnUserDeleted.md) | `__property TsgcWSE2EEClientOnUserDeleted * OnE2EEUserDeleted;` |
| `OnE2EEGroupMessageText: TsgcWSE2EEOnGroupMessageText` | [TsgcWSE2EEOnGroupMessageText](../types/TsgcWSE2EEOnGroupMessageText.md) | `__property TsgcWSE2EEOnGroupMessageText * OnE2EEGroupMessageText;` |
| `OnE2EEGroupMessageBinary: TsgcWSE2EEOnGroupMessageBinary` | [TsgcWSE2EEOnGroupMessageBinary](../types/TsgcWSE2EEOnGroupMessageBinary.md) | `__property TsgcWSE2EEOnGroupMessageBinary * OnE2EEGroupMessageBinary;` |
| `OnE2EEGroupMessageAck: TsgcWSE2EEOnGroupMessageAckEvent` | [TsgcWSE2EEOnGroupMessageAckEvent](../types/TsgcWSE2EEOnGroupMessageAckEvent.md) | `__property TsgcWSE2EEOnGroupMessageAckEvent OnE2EEGroupMessageAck;` |
| `OnE2EEGroupCreated: TsgcWSE2EEOnGroupCreated` | [TsgcWSE2EEOnGroupCreated](../types/TsgcWSE2EEOnGroupCreated.md) | `__property TsgcWSE2EEOnGroupCreated * OnE2EEGroupCreated;` |
| `OnE2EEGroupDeleted: TsgcWSE2EEOnGroupDeleted` | [TsgcWSE2EEOnGroupDeleted](../types/TsgcWSE2EEOnGroupDeleted.md) | `__property TsgcWSE2EEOnGroupDeleted * OnE2EEGroupDeleted;` |
| `OnE2EEGroupJoin: TsgcWSE2EEOnGroupJoin` | [TsgcWSE2EEOnGroupJoin](../types/TsgcWSE2EEOnGroupJoin.md) | `__property TsgcWSE2EEOnGroupJoin * OnE2EEGroupJoin;` |
| `OnE2EEGroupLeave: TsgcWSE2EEOnGroupLeave` | [TsgcWSE2EEOnGroupLeave](../types/TsgcWSE2EEOnGroupLeave.md) | `__property TsgcWSE2EEOnGroupLeave * OnE2EEGroupLeave;` |
| `OnE2EEGroupMemberJoin: TsgcWSE2EEOnGroupMemberJoin` | [TsgcWSE2EEOnGroupMemberJoin](../types/TsgcWSE2EEOnGroupMemberJoin.md) | `__property TsgcWSE2EEOnGroupMemberJoin * OnE2EEGroupMemberJoin;` |
| `OnE2EEGroupMemberLeave: TsgcWSE2EEOnGroupMemberLeave` | [TsgcWSE2EEOnGroupMemberLeave](../types/TsgcWSE2EEOnGroupMemberLeave.md) | `__property TsgcWSE2EEOnGroupMemberLeave * OnE2EEGroupMemberLeave;` |
| `OnSubscription: TsgcWSSubscriptionEvent` | [TsgcWSSubscriptionEvent](../types/TsgcWSSubscriptionEvent.md) | `__property TsgcWSSubscriptionEvent OnSubscription;` |
| `OnUnSubscription: TsgcWSSubscriptionEvent` | [TsgcWSSubscriptionEvent](../types/TsgcWSSubscriptionEvent.md) | `__property TsgcWSSubscriptionEvent OnUnSubscription;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |

## Methods

Delphi

```pascal
function SendDirectMessage(const aTo, aText: string): string;
function SendGroupMessage(const aGroup, aText: string): string;
function CreateGroup(const aGroup: string; aTimeout: Integer = 10000) : TsgcE2EE_Group;
function DeleteGroup(const aGroup: string; aTimeout: Integer = 10000): Boolean;
function JoinGroup(const aGroup: string; aTimeout: Integer = 10000) : Boolean;
function LeaveGroup(const aGroup: string; aTimeout: Integer = 10000): Boolean;
procedure Subscribe(const aChannel: String; const aGuid: String = '');
procedure UnSubscribe(const aChannel: String; const aGuid: String = '');
procedure WriteData(const aText: String);
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
UnicodeString __fastcall SendDirectMessage(const UnicodeString aTo, const UnicodeString aText);
UnicodeString __fastcall SendGroupMessage(const UnicodeString aGroup, const UnicodeString aText);
TsgcE2EE_Group * __fastcall CreateGroup(const UnicodeString aGroup, int aTimeout = 10000);
bool __fastcall DeleteGroup(const UnicodeString aGroup, int aTimeout = 10000);
bool __fastcall JoinGroup(const UnicodeString aGroup, int aTimeout = 10000);
bool __fastcall LeaveGroup(const UnicodeString aGroup, int aTimeout = 10000);
void __fastcall Subscribe(const UnicodeString aChannel, const UnicodeString aGuid = '');
void __fastcall UnSubscribe(const UnicodeString aChannel, const UnicodeString aGuid = '');
void __fastcall WriteData(const UnicodeString aText);
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

