# TIdSchedulerOfThread

kind: class
unit: IdSchedulerOfThread

## Properties

| Delphi | Type |
| --- | --- |
| `ThreadClass: TIdThreadWithTaskClass` | [TIdThreadWithTaskClass](./TIdThreadWithTaskClass.md) |
| `MaxThreads: Integer` | `Integer` |
| `ThreadPriority: TIdThreadPriority` | `TIdThreadPriority` |
| `ActiveYarns: TIdYarnThreadList (read-only)` | `TIdYarnThreadList` |
| `Version: string (read-only)` | `string` |

## Methods

```pascal
function NewThread: TIdThreadWithTask;
function NewYarn(AThread: TIdThreadWithTask = nil): TIdYarnOfThread;
procedure StartYarn(AYarn: TIdYarn; ATask: TIdTask);
procedure TerminateYarn(AYarn: TIdYarn);
function AcquireYarn: TIdYarn;
procedure Init;
procedure ReleaseYarn(AYarn: TIdYarn);
procedure TerminateAllYarns;
procedure RemoveFreeNotification(AComponent: TComponent);
```

