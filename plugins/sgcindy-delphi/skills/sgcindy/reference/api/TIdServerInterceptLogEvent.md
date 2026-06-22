# TIdServerInterceptLogEvent

unit: IdServerInterceptLogEvent

Add `IdServerInterceptLogEvent` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `LogTime: Boolean` | `Boolean` | `__property bool LogTime;` |
| `ReplaceCRLF: Boolean` | `Boolean` | `__property bool ReplaceCRLF;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnLogString: TIdOnLogString` | [TIdOnLogString](../types/TIdOnLogString.md) | `__property TIdOnLogString * OnLogString;` |

## Methods

Delphi

```pascal
procedure DoLogWriteString(const AText: string);
procedure Init;
function Accept(AConnection: TComponent): TIdConnectionIntercept;
procedure LogWriteString(const AText: string);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall DoLogWriteString(const UnicodeString AText);
void __fastcall Init();
TIdConnectionIntercept * __fastcall Accept(TComponent * AConnection);
void __fastcall LogWriteString(const UnicodeString AText);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

