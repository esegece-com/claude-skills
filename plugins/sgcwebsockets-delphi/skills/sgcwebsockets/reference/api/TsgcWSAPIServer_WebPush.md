# TsgcWSAPIServer_WebPush

unit: sgcWebSocket_Server_APIs
Edition: requires SGC_WEBPUSH

Add `sgcWebSocket_Server_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `WebPush: TsgcWSWebPush_Options` | [TsgcWSWebPush_Options](../types/TsgcWSWebPush_Options.md) | `__property TsgcWSWebPush_Options * WebPush;` |
| `Server: TsgcWSComponent_Server` | [TsgcWSComponent_Server](../types/TsgcWSComponent_Server.md) | `__property TsgcWSComponent_Server * Server;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `Subscriptions: TsgcWebPushSubscriptions` | [TsgcWebPushSubscriptions](../types/TsgcWebPushSubscriptions.md) | `__property TsgcWebPushSubscriptions * Subscriptions;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnWebPushSubscription: TsgcWSWebPushSubscription` | [TsgcWSWebPushSubscription](../types/TsgcWSWebPushSubscription.md) | `__property TsgcWSWebPushSubscription * OnWebPushSubscription;` |
| `OnWebPushUnsubscription: TsgcWSWebPushUnsubscription` | [TsgcWSWebPushUnsubscription](../types/TsgcWSWebPushUnsubscription.md) | `__property TsgcWSWebPushUnsubscription * OnWebPushUnsubscription;` |
| `OnWebPushSendNotificationException: TsgcWSWebPushSendNotificationException` | [TsgcWSWebPushSendNotificationException](../types/TsgcWSWebPushSendNotificationException.md) | `__property TsgcWSWebPushSendNotificationException * OnWebPushSendNotificationException;` |
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
procedure SendNotification(const aSubscription : TsgcHTTP_API_WebPush_PushSubscription; const aMessage: TsgcWebPushMessage);
procedure BroadcastNotification(const aMessage : TsgcWebPushMessage);
procedure KeepAlive(const aConnection: TsgcWSConnection; const aMessage: string);
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall SendNotification(const TsgcHTTP_API_WebPush_PushSubscription * aSubscription, const TsgcWebPushMessage * aMessage);
void __fastcall BroadcastNotification(const TsgcWebPushMessage * aMessage);
void __fastcall KeepAlive(const TsgcWSConnection * aConnection, const UnicodeString aMessage);
void __fastcall QueueClear();
```

