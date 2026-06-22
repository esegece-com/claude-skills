# TsgcWSAPI_Pusher

unit: sgcWebSocket_APIs
Edition: Standard

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Pusher: TsgcWSPusher_Options` | [TsgcWSPusher_Options](../types/TsgcWSPusher_Options.md) | `__property TsgcWSPusher_Options * Pusher;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |
| `OnPusherConnect: TsgcWSPusherConnectEvent` | [TsgcWSPusherConnectEvent](../types/TsgcWSPusherConnectEvent.md) | `__property TsgcWSPusherConnectEvent OnPusherConnect;` |
| `OnPusherError: TsgcWSPusherErrorEvent` | [TsgcWSPusherErrorEvent](../types/TsgcWSPusherErrorEvent.md) | `__property TsgcWSPusherErrorEvent OnPusherError;` |
| `OnPusherEvent: TsgcWSPusherEventEvent` | [TsgcWSPusherEventEvent](../types/TsgcWSPusherEventEvent.md) | `__property TsgcWSPusherEventEvent OnPusherEvent;` |
| `OnPusherSubscribe: TsgcWSPusherSubscribeEvent` | [TsgcWSPusherSubscribeEvent](../types/TsgcWSPusherSubscribeEvent.md) | `__property TsgcWSPusherSubscribeEvent OnPusherSubscribe;` |
| `OnPusherAuthentication: TsgcWSPusherAuthenticationEvent` | [TsgcWSPusherAuthenticationEvent](../types/TsgcWSPusherAuthenticationEvent.md) | `__property TsgcWSPusherAuthenticationEvent OnPusherAuthentication;` |
| `OnPusherCacheMiss: TsgcWSPusherCacheMissEvent` | [TsgcWSPusherCacheMissEvent](../types/TsgcWSPusherCacheMissEvent.md) | `__property TsgcWSPusherCacheMissEvent OnPusherCacheMiss;` |
| `OnPusherMemberAdded: TsgcWSPusherMemberEvent` | [TsgcWSPusherMemberEvent](../types/TsgcWSPusherMemberEvent.md) | `__property TsgcWSPusherMemberEvent OnPusherMemberAdded;` |
| `OnPusherMemberRemoved: TsgcWSPusherMemberEvent` | [TsgcWSPusherMemberEvent](../types/TsgcWSPusherMemberEvent.md) | `__property TsgcWSPusherMemberEvent OnPusherMemberRemoved;` |
| `OnPusherSubscriptionCount: TsgcWSPusherSubscriptionCountEvent` | [TsgcWSPusherSubscriptionCountEvent](../types/TsgcWSPusherSubscriptionCountEvent.md) | `__property TsgcWSPusherSubscriptionCountEvent OnPusherSubscriptionCount;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |

## Methods

Delphi

```pascal
procedure Ping(const aData: string = '{}');
procedure Subscribe(const aChannel: String; aChannelType: TsgcWSPusherChannels = pscPublicChannel; aData: String = '');
procedure UnSubscribe(const aChannel: String; aChannelType: TsgcWSPusherChannels = pscPublicChannel);
procedure Publish(const aEvent, aChannel: string; aChannelType: TsgcWSPusherChannels = pscPublicChannel; const aData: string = '{}');
function TriggerEvent(const aEventName, aChannel, aData: string; const aSocketId: string = ''; const aInfo: string = ''): string;
function TriggerBatchEvents(const aBatch: string): string;
function GetChannels(const aFilterByPrefix: string = ''; const aInfo: string = ''): string;
function GetChannel(const aChannel: string; const aInfo: string = ''): string;
function GetUsers(const aChannel: string): string;
function TerminateUserConnections(const aUserId: string): string;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Ping(const UnicodeString aData = '{}');
void __fastcall Subscribe(const UnicodeString aChannel, TsgcWSPusherChannels * aChannelType = pscPublicChannel, UnicodeString aData = '');
void __fastcall UnSubscribe(const UnicodeString aChannel, TsgcWSPusherChannels * aChannelType = pscPublicChannel);
void __fastcall Publish(const UnicodeString aEvent, const UnicodeString aChannel, TsgcWSPusherChannels * aChannelType = pscPublicChannel, const UnicodeString aData = '{}');
UnicodeString __fastcall TriggerEvent(const UnicodeString aEventName, const UnicodeString aChannel, const UnicodeString aData, const UnicodeString aSocketId = '', const UnicodeString aInfo = '');
UnicodeString __fastcall TriggerBatchEvents(const UnicodeString aBatch);
UnicodeString __fastcall GetChannels(const UnicodeString aFilterByPrefix = '', const UnicodeString aInfo = '');
UnicodeString __fastcall GetChannel(const UnicodeString aChannel, const UnicodeString aInfo = '');
UnicodeString __fastcall GetUsers(const UnicodeString aChannel);
UnicodeString __fastcall TerminateUserConnections(const UnicodeString aUserId);
void __fastcall QueueClear();
```

