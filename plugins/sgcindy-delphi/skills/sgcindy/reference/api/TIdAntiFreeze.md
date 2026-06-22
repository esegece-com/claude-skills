# TIdAntiFreeze

unit: IdAntiFreeze

Add `IdAntiFreeze` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Active: boolean` | `boolean` | `__property bool Active;` |
| `ApplicationHasPriority: Boolean` | `Boolean` | `__property bool ApplicationHasPriority;` |
| `IdleTimeOut: integer` | `integer` | `__property int IdleTimeOut;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnlyWhenIdle: Boolean` | `Boolean` | `__property bool OnlyWhenIdle;` |

## Methods

Delphi

```pascal
procedure Process;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Process();
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

