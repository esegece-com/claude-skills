# TsgcWSPServer_WAMP

unit: sgcWebSocket_Protocols
Edition: Professional

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Server: TsgcWSComponent_Server` | [TsgcWSComponent_Server](../types/TsgcWSComponent_Server.md) | `__property TsgcWSComponent_Server * Server;` |
| `Broker: TsgcWSProtocol_Broker_Server` | [TsgcWSProtocol_Broker_Server](../types/TsgcWSProtocol_Broker_Server.md) | `__property TsgcWSProtocol_Broker_Server * Broker;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
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
| `OnRawMessage: TsgcOnWhatsAppServerMessage` | [TsgcOnWhatsAppServerMessage](../types/TsgcOnWhatsAppServerMessage.md) | `__property TsgcOnWhatsAppServerMessage * OnRawMessage;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |
| `OnBeforeSubscription: TsgcWSBeforeSubscriptionEvent` | [TsgcWSBeforeSubscriptionEvent](../types/TsgcWSBeforeSubscriptionEvent.md) | `__property TsgcWSBeforeSubscriptionEvent OnBeforeSubscription;` |
| `OnSubscription: TsgcWSSubscriptionEvent` | [TsgcWSSubscriptionEvent](../types/TsgcWSSubscriptionEvent.md) | `__property TsgcWSSubscriptionEvent OnSubscription;` |
| `OnUnSubscription: TsgcWSSubscriptionEvent` | [TsgcWSSubscriptionEvent](../types/TsgcWSSubscriptionEvent.md) | `__property TsgcWSSubscriptionEvent OnUnSubscription;` |
| `OnCall: TsgcWSCallEvent` | [TsgcWSCallEvent](../types/TsgcWSCallEvent.md) | `__property TsgcWSCallEvent OnCall;` |
| `OnBeforeCancelCall: TsgcWSBeforeCancelCallEvent` | [TsgcWSBeforeCancelCallEvent](../types/TsgcWSBeforeCancelCallEvent.md) | `__property TsgcWSBeforeCancelCallEvent OnBeforeCancelCall;` |
| `OnPrefix: TsgcWSPrefixEvent` | [TsgcWSPrefixEvent](../types/TsgcWSPrefixEvent.md) | `__property TsgcWSPrefixEvent OnPrefix;` |

## Methods

Delphi

```pascal
procedure CallResult(const aCallId: String; const aResult: String = '');
procedure CallProgressResult(const aCallId: String; const aResult: String = '');
procedure CallError(const aCallId, aErrorURI, aErrorDesc: String; const aErrorDetails: String = '');
procedure Event(const aTopicURI: String; const aEvent: String = '');
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall CallResult(const UnicodeString aCallId, const UnicodeString aResult = '');
void __fastcall CallProgressResult(const UnicodeString aCallId, const UnicodeString aResult = '');
void __fastcall CallError(const UnicodeString aCallId, const UnicodeString aErrorURI, const UnicodeString aErrorDesc, const UnicodeString aErrorDetails = '');
void __fastcall Event(const UnicodeString aTopicURI, const UnicodeString aEvent = '');
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

