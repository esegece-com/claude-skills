# TsgcLib_RCON

unit: sgcLibs
Edition: Standard

Add `sgcLibs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `RCON_Options: TsgcRCON_Options` | [TsgcRCON_Options](../types/TsgcRCON_Options.md) | `__property TsgcRCON_Options * RCON_Options;` |
| `NotifyEvents: TwsNotifyEvent` | [TwsNotifyEvent](../types/TwsNotifyEvent.md) | `__property TwsNotifyEvent NotifyEvents;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnConnect;` |
| `OnDisconnect: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDisconnect;` |
| `OnAuthenticate: TsgcRCONAuthenticateEvent` | [TsgcRCONAuthenticateEvent](../types/TsgcRCONAuthenticateEvent.md) | `__property TsgcRCONAuthenticateEvent OnAuthenticate;` |
| `OnResponse: TsgcRCONResponseEvent` | [TsgcRCONResponseEvent](../types/TsgcRCONResponseEvent.md) | `__property TsgcRCONResponseEvent OnResponse;` |
| `OnException: TsgcRCONExceptionEvent` | [TsgcRCONExceptionEvent](../types/TsgcRCONExceptionEvent.md) | `__property TsgcRCONExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure ExecCommand(const aValue: string; const aId: Integer = 0);
```

C++Builder

```cpp
void __fastcall ExecCommand(const UnicodeString aValue, const int aId = 0);
```

