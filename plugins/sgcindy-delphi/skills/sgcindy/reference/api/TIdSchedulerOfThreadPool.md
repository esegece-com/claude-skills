# TIdSchedulerOfThreadPool

unit: IdSchedulerOfThreadPool

Add `IdSchedulerOfThreadPool` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `PoolSize: Integer` | `Integer` | `__property int PoolSize;` |
| `ThreadClass: TIdThreadWithTaskClass` | [TIdThreadWithTaskClass](../types/TIdThreadWithTaskClass.md) | `__property TIdThreadWithTaskClass * ThreadClass;` |
| `MaxThreads: Integer` | `Integer` | `__property int MaxThreads;` |
| `ThreadPriority: TIdThreadPriority` | `TIdThreadPriority` | `__property TIdThreadPriority * ThreadPriority;` |
| `ActiveYarns: TIdYarnThreadList (read-only)` | `TIdYarnThreadList` | `__property TIdYarnThreadList * ActiveYarns /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
function AcquireYarn: TIdYarn;
procedure Init;
function NewThread: TIdThreadWithTask;
procedure ReleaseYarn(AYarn: TIdYarn);
procedure TerminateAllYarns;
function NewYarn(AThread: TIdThreadWithTask = nil): TIdYarnOfThread;
procedure StartYarn(AYarn: TIdYarn; ATask: TIdTask);
procedure TerminateYarn(AYarn: TIdYarn);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
TIdYarn * __fastcall AcquireYarn();
void __fastcall Init();
TIdThreadWithTask * __fastcall NewThread();
void __fastcall ReleaseYarn(TIdYarn * AYarn);
void __fastcall TerminateAllYarns();
TIdYarnOfThread * __fastcall NewYarn(TIdThreadWithTask * AThread = nil);
void __fastcall StartYarn(TIdYarn * AYarn, TIdTask * ATask);
void __fastcall TerminateYarn(TIdYarn * AYarn);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

