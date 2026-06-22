# TsgcHTMX_Router

unit: sgcHTMX_Router
Edition: All-Access

Add `sgcHTMX_Router` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Routes: TsgcHTMX_Routes` | [TsgcHTMX_Routes](../types/TsgcHTMX_Routes.md) | `__property TsgcHTMX_Routes * Routes;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function HandleRequest(const aPath, aMethod, aGuid: string; const aParams: TStringList): string;
```

C++Builder

```cpp
UnicodeString __fastcall HandleRequest(const UnicodeString aPath, const UnicodeString aMethod, const UnicodeString aGuid, const TStringList * aParams);
```

