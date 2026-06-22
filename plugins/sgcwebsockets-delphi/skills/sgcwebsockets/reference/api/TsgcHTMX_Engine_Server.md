# TsgcHTMX_Engine_Server

unit: sgcHTMX_Engine_Server
Edition: requires SGC_HTMX

Add `sgcHTMX_Engine_Server` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Template: TsgcHTMLTemplate_HTMX` | [TsgcHTMLTemplate_HTMX](../types/TsgcHTMLTemplate_HTMX.md) | `__property TsgcHTMLTemplate_HTMX * Template;` |
| `Router: TsgcHTMX_Router` | [TsgcHTMX_Router](../types/TsgcHTMX_Router.md) | `__property TsgcHTMX_Router * Router;` |
| `Server: TsgcWSHTTPServer` | [TsgcWSHTTPServer](../types/TsgcWSHTTPServer.md) | `__property TsgcWSHTTPServer * Server;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnHTMXMessage: TsgcHTMXMessageEvent` | [TsgcHTMXMessageEvent](../types/TsgcHTMXMessageEvent.md) | `__property TsgcHTMXMessageEvent OnHTMXMessage;` |

## Methods

Delphi

```pascal
procedure PushFragment(const aGuid: string; const aFragment: TsgcHTMX_Fragment);
procedure BroadcastFragment(const aFragment: TsgcHTMX_Fragment; const aChannel: string = ''; const aExclude: string = '');
function GetPageHTML: string;
```

C++Builder

```cpp
void __fastcall PushFragment(const UnicodeString aGuid, const TsgcHTMX_Fragment * aFragment);
void __fastcall BroadcastFragment(const TsgcHTMX_Fragment * aFragment, const UnicodeString aChannel = '', const UnicodeString aExclude = '');
UnicodeString __fastcall GetPageHTML();
```

