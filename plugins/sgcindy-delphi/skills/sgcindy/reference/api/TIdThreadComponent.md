# TIdThreadComponent

unit: IdThreadComponent

Add `IdThreadComponent` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `DataObject: TObject` | `TObject` | `__property TObject * DataObject;` |
| `DataValue: PtrInt` | `PtrInt` | `__property PtrInt DataValue;` |
| `Data: TObject` | `TObject` | `__property TObject * Data;` |
| `Handle: TIdThreadHandle (read-only)` | `TIdThreadHandle` | `__property TIdThreadHandle * Handle /* read-only */;` |
| `ReturnValue: Integer` | `Integer` | `__property int ReturnValue;` |
| `Stopped: Boolean (read-only)` | `Boolean` | `__property bool Stopped /* read-only */;` |
| `Suspended: Boolean (read-only)` | `Boolean` | `__property bool Suspended /* read-only */;` |
| `TerminatingException: string (read-only)` | `string` | `__property UnicodeString TerminatingException /* read-only */;` |
| `TerminatingExceptionClass: TClass (read-only)` | `TClass` | `__property TClass * TerminatingExceptionClass /* read-only */;` |
| `Terminated: Boolean (read-only)` | `Boolean` | `__property bool Terminated /* read-only */;` |
| `Priority: TIdThreadPriority` | `TIdThreadPriority` | `__property TIdThreadPriority * Priority;` |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `Loop: Boolean` | `Boolean` | `__property bool Loop;` |
| `StopMode: TIdThreadStopMode` | [TIdThreadStopMode](../types/TIdThreadStopMode.md) | `__property TIdThreadStopMode * StopMode;` |
| `ThreadName: string` | `string` | `__property UnicodeString ThreadName;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnAfterExecute: TIdNotifyThreadComponentEvent` | [TIdNotifyThreadComponentEvent](../types/TIdNotifyThreadComponentEvent.md) | `__property TIdNotifyThreadComponentEvent OnAfterExecute;` |
| `OnAfterRun: TIdNotifyThreadComponentEvent` | [TIdNotifyThreadComponentEvent](../types/TIdNotifyThreadComponentEvent.md) | `__property TIdNotifyThreadComponentEvent OnAfterRun;` |
| `OnBeforeExecute: TIdNotifyThreadComponentEvent` | [TIdNotifyThreadComponentEvent](../types/TIdNotifyThreadComponentEvent.md) | `__property TIdNotifyThreadComponentEvent OnBeforeExecute;` |
| `OnBeforeRun: TIdNotifyThreadComponentEvent` | [TIdNotifyThreadComponentEvent](../types/TIdNotifyThreadComponentEvent.md) | `__property TIdNotifyThreadComponentEvent OnBeforeRun;` |
| `OnCleanup: TIdNotifyThreadComponentEvent` | [TIdNotifyThreadComponentEvent](../types/TIdNotifyThreadComponentEvent.md) | `__property TIdNotifyThreadComponentEvent OnCleanup;` |
| `OnException: TIdExceptionThreadComponentEvent` | [TIdExceptionThreadComponentEvent](../types/TIdExceptionThreadComponentEvent.md) | `__property TIdExceptionThreadComponentEvent OnException;` |
| `OnHandleRunException: TIdExceptionThreadComponentEventEx` | [TIdExceptionThreadComponentEventEx](../types/TIdExceptionThreadComponentEventEx.md) | `__property TIdExceptionThreadComponentEventEx * OnHandleRunException;` |
| `OnRun: TIdNotifyThreadComponentEvent` | [TIdNotifyThreadComponentEvent](../types/TIdNotifyThreadComponentEvent.md) | `__property TIdNotifyThreadComponentEvent OnRun;` |
| `OnStopped: TIdNotifyThreadComponentEvent` | [TIdNotifyThreadComponentEvent](../types/TIdNotifyThreadComponentEvent.md) | `__property TIdNotifyThreadComponentEvent OnStopped;` |
| `OnTerminate: TIdNotifyThreadComponentEvent` | [TIdNotifyThreadComponentEvent](../types/TIdNotifyThreadComponentEvent.md) | `__property TIdNotifyThreadComponentEvent OnTerminate;` |

## Methods

Delphi

```pascal
procedure Start;
procedure Stop;
procedure Synchronize(AMethod: TThreadMethod);
procedure Terminate;
procedure TerminateAndWaitFor;
function WaitFor: UInt32;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Start();
void __fastcall Stop();
void __fastcall Synchronize(TThreadMethod * AMethod);
void __fastcall Terminate();
void __fastcall TerminateAndWaitFor();
UInt32 __fastcall WaitFor();
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

