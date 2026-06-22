# TIdIPAddrMonThread

kind: class
unit: IdIPAddrMon

## Properties

| Delphi | Type |
| --- | --- |
| `DataObject: TObject` | `TObject` |
| `DataValue: PtrInt` | `PtrInt` |
| `Data: TObject` | `TObject` |
| `Loop: Boolean` | `Boolean` |
| `Name: string` | `string` |
| `ReturnValue: Integer` | `Integer` |
| `StopMode: TIdThreadStopMode` | [TIdThreadStopMode](./TIdThreadStopMode.md) |
| `Stopped: Boolean (read-only)` | `Boolean` |
| `Terminated: Boolean (read-only)` | `Boolean` |
| `TerminatingException: string (read-only)` | `string` |
| `TerminatingExceptionClass: TClass (read-only)` | `TClass` |
| `Yarn: TIdYarn` | [TIdYarn](./TIdYarn.md) |

## Events

| Delphi | Type |
| --- | --- |
| `OnException: TIdExceptionThreadEvent` | [TIdExceptionThreadEvent](./TIdExceptionThreadEvent.md) |
| `OnStopped: TIdNotifyThreadEvent` | [TIdNotifyThreadEvent](./TIdNotifyThreadEvent.md) |

## Methods

```pascal
procedure Start;
procedure Stop;
procedure Synchronize(Method: TThreadMethod);
procedure Terminate;
procedure TerminateAndWaitFor;
```

