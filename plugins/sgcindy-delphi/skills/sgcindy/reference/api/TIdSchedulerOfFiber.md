# TIdSchedulerOfFiber

unit: IdSchedulerOfFiber

Add `IdSchedulerOfFiber` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `FiberWeaver: TIdFiberWeaver` | [TIdFiberWeaver](../types/TIdFiberWeaver.md) | `__property TIdFiberWeaver * FiberWeaver;` |
| `ActiveYarns: TIdYarnThreadList (read-only)` | `TIdYarnThreadList` | `__property TIdYarnThreadList * ActiveYarns /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function AcquireYarn : TIdYarn;
procedure StartYarn( AYarn: TIdYarn; ATask: TIdTask );
procedure TerminateYarn( AYarn: TIdYarn );
procedure Init;
procedure ReleaseYarn(AYarn: TIdYarn);
procedure TerminateAllYarns;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
TIdYarn * __fastcall AcquireYarn();
void __fastcall StartYarn(TIdYarn * AYarn, TIdTask * ATask);
void __fastcall TerminateYarn(TIdYarn * AYarn);
void __fastcall Init();
void __fastcall ReleaseYarn(TIdYarn * AYarn);
void __fastcall TerminateAllYarns();
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

