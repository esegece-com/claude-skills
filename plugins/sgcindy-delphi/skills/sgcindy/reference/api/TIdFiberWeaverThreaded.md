# TIdFiberWeaverThreaded

unit: IdFiberWeaverThreaded

Add `IdFiberWeaverThreaded` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `ThreadScheduler: TIdSchedulerOfThread` | [TIdSchedulerOfThread](../types/TIdSchedulerOfThread.md) | `__property TIdSchedulerOfThread * ThreadScheduler;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure Add( AFiber: TIdFiber );
function WaitForFibers( ATimeout: Cardinal = Infinite ): Boolean;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Add(TIdFiber * AFiber);
bool __fastcall WaitForFibers(unsigned int ATimeout = Infinite);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

