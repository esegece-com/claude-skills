# TsgcWebPush_Client

unit: sgcHTTP
Edition: requires SGC_WEBPUSH

Add `sgcHTTP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `VAPID: TsgcHTTP_API_WebPush_VAPID_Options` | [TsgcHTTP_API_WebPush_VAPID_Options](../types/TsgcHTTP_API_WebPush_VAPID_Options.md) | `__property TsgcHTTP_API_WebPush_VAPID_Options * VAPID;` |
| `WebPushOptions: TsgcHTTP_API_WebPush_Client_Options` | [TsgcHTTP_API_WebPush_Client_Options](../types/TsgcHTTP_API_WebPush_Client_Options.md) | `__property TsgcHTTP_API_WebPush_Client_Options * WebPushOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure SendNotification(const aPushSubscription : TsgcHTTP_API_WebPush_PushSubscription; const aText: string);
```

C++Builder

```cpp
void __fastcall SendNotification(const TsgcHTTP_API_WebPush_PushSubscription * aPushSubscription, const UnicodeString aText);
```

