# TIdFiberWeaverInline

unit: IdFiberWeaverInline

Add `IdFiberWeaverInline` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `FreeFibersOnCompletion: Boolean` | `Boolean` | `__property bool FreeFibersOnCompletion;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnIdle: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnIdle;` |
| `OnSwitch: TIdFiberNotifyEvent` | [TIdFiberNotifyEvent](../types/TIdFiberNotifyEvent.md) | `__property TIdFiberNotifyEvent OnSwitch;` |

## Methods

Delphi

```pascal
procedure Add(AFiber: TIdFiber);
function HasFibers: Boolean;
function ProcessInThisThread: Boolean;
function WaitForFibers( ATimeout: Cardinal = Infinite ): Boolean;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Add(TIdFiber * AFiber);
bool __fastcall HasFibers();
bool __fastcall ProcessInThisThread();
bool __fastcall WaitForFibers(unsigned int ATimeout = Infinite);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

