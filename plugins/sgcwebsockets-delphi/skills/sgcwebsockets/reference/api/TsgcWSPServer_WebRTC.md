# TsgcWSPServer_WebRTC

unit: sgcWebSocket_Protocols
Edition: Professional and higher

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Server: TsgcWSComponent_Server` | [TsgcWSComponent_Server](../types/TsgcWSComponent_Server.md) | `__property TsgcWSComponent_Server * Server;` |
| `Broker: TsgcWSProtocol_Broker_Server` | [TsgcWSProtocol_Broker_Server](../types/TsgcWSProtocol_Broker_Server.md) | `__property TsgcWSProtocol_Broker_Server * Broker;` |
| `WebRTC: TsgcWSWebRTC_Options` | [TsgcWSWebRTC_Options](../types/TsgcWSWebRTC_Options.md) | `__property TsgcWSWebRTC_Options * WebRTC;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `WebRTCSubscriptions: TsgcThreadSafeStringList` | [TsgcThreadSafeStringList](../types/TsgcThreadSafeStringList.md) | `__property TsgcThreadSafeStringList * WebRTCSubscriptions;` |
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

## Methods

Delphi

```pascal
procedure Broadcast(aMessage: string; aChannel: string = ''; Exclude: String = ''; Include: String = '');
function WriteData(aGuid, aMessage: string): Boolean;
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Broadcast(UnicodeString aMessage, UnicodeString aChannel = '', UnicodeString Exclude = '', UnicodeString Include = '');
bool __fastcall WriteData(UnicodeString aGuid, UnicodeString aMessage);
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

