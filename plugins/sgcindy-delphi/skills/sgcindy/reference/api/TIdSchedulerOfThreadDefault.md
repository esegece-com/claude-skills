# TIdSchedulerOfThreadDefault

unit: IdSchedulerOfThreadDefault

Add `IdSchedulerOfThreadDefault` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `ThreadClass: TIdThreadWithTaskClass` | [TIdThreadWithTaskClass](../types/TIdThreadWithTaskClass.md) | `__property TIdThreadWithTaskClass * ThreadClass;` |
| `MaxThreads: Integer` | `Integer` | `__property int MaxThreads;` |
| `ThreadPriority: TIdThreadPriority` | `TIdThreadPriority` | `__property TIdThreadPriority * ThreadPriority;` |
| `ActiveYarns: TIdYarnThreadList (read-only)` | `TIdYarnThreadList` | `__property TIdYarnThreadList * ActiveYarns /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function AcquireYarn: TIdYarn;
procedure ReleaseYarn(AYarn: TIdYarn);
function NewThread: TIdThreadWithTask;
function NewYarn(AThread: TIdThreadWithTask = nil): TIdYarnOfThread;
procedure StartYarn(AYarn: TIdYarn; ATask: TIdTask);
procedure TerminateYarn(AYarn: TIdYarn);
procedure Init;
procedure TerminateAllYarns;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
TIdYarn * __fastcall AcquireYarn();
void __fastcall ReleaseYarn(TIdYarn * AYarn);
TIdThreadWithTask * __fastcall NewThread();
TIdYarnOfThread * __fastcall NewYarn(TIdThreadWithTask * AThread = nil);
void __fastcall StartYarn(TIdYarn * AYarn, TIdTask * ATask);
void __fastcall TerminateYarn(TIdYarn * AYarn);
void __fastcall Init();
void __fastcall TerminateAllYarns();
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

