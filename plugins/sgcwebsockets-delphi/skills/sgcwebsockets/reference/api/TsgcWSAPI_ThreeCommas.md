# TsgcWSAPI_ThreeCommas

unit: sgcWebSocket_APIs

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `ThreeCommas: TsgcWSThreeCommas_Options` | [TsgcWSThreeCommas_Options](../types/TsgcWSThreeCommas_Options.md) | `__property TsgcWSThreeCommas_Options * ThreeCommas;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `REST_API: TsgcHTTP_API_3Commas_Rest` | [TsgcHTTP_API_3Commas_Rest](../types/TsgcHTTP_API_3Commas_Rest.md) | `__property TsgcHTTP_API_3Commas_Rest * REST_API;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnThreeCommasConnect: TsgcWSThreeCommasConnectEvent` | [TsgcWSThreeCommasConnectEvent](../types/TsgcWSThreeCommasConnectEvent.md) | `__property TsgcWSThreeCommasConnectEvent OnThreeCommasConnect;` |
| `OnThreeCommasConfirmSubscription: TsgcWSThreeCommasSubscribedEvent` | [TsgcWSThreeCommasSubscribedEvent](../types/TsgcWSThreeCommasSubscribedEvent.md) | `__property TsgcWSThreeCommasSubscribedEvent OnThreeCommasConfirmSubscription;` |
| `OnThreeCommasRejectSubscription: TsgcWSThreeCommasRejectSubscriptionEvent` | [TsgcWSThreeCommasRejectSubscriptionEvent](../types/TsgcWSThreeCommasRejectSubscriptionEvent.md) | `__property TsgcWSThreeCommasRejectSubscriptionEvent OnThreeCommasRejectSubscription;` |
| `OnThreeCommasMessage: TsgcWSThreeCommasMessageEvent` | [TsgcWSThreeCommasMessageEvent](../types/TsgcWSThreeCommasMessageEvent.md) | `__property TsgcWSThreeCommasMessageEvent OnThreeCommasMessage;` |
| `OnThreeCommasPing: TsgcWSThreeCommasPingEvent` | [TsgcWSThreeCommasPingEvent](../types/TsgcWSThreeCommasPingEvent.md) | `__property TsgcWSThreeCommasPingEvent OnThreeCommasPing;` |
| `OnThreeCommasHTTPException: TsgcWSThreeCommasHTTPExceptionEvent` | [TsgcWSThreeCommasHTTPExceptionEvent](../types/TsgcWSThreeCommasHTTPExceptionEvent.md) | `__property TsgcWSThreeCommasHTTPExceptionEvent OnThreeCommasHTTPException;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure SubscribeSmartTrades;
procedure SubscribeDeals;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall SubscribeSmartTrades();
void __fastcall SubscribeDeals();
void __fastcall QueueClear();
```

