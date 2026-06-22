# TIdScheduler

kind: class
unit: IdScheduler

## Properties

| Delphi | Type |
| --- | --- |
| `ActiveYarns: TIdYarnThreadList (read-only)` | `TIdYarnThreadList` |
| `Version: string (read-only)` | `string` |

## Methods

```pascal
function AcquireYarn: TIdYarn;
procedure Init;
procedure ReleaseYarn(AYarn: TIdYarn);
procedure StartYarn(AYarn: TIdYarn; ATask: TIdTask);
procedure TerminateYarn(AYarn: TIdYarn);
procedure TerminateAllYarns;
procedure RemoveFreeNotification(AComponent: TComponent);
```

