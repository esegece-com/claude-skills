# TsgcWSCircuitBreaker

kind: class
unit: sgcWebSocket_CircuitBreaker

## Properties

| Delphi | Type |
| --- | --- |
| `Enabled: Boolean` | `Boolean` |
| `DefaultKey: string` | `string` |
| `ServerKey: string` | `string` |
| `Thresholds: TsgcCircuitBreakerThresholds` | [TsgcCircuitBreakerThresholds](./TsgcCircuitBreakerThresholds.md) |
| `TimeWindow: TsgcCircuitBreakerWindow` | [TsgcCircuitBreakerWindow](./TsgcCircuitBreakerWindow.md) |
| `Recovery: TsgcCircuitBreakerRecovery` | [TsgcCircuitBreakerRecovery](./TsgcCircuitBreakerRecovery.md) |
| `Fallback: TsgcCircuitBreakerFallback` | [TsgcCircuitBreakerFallback](./TsgcCircuitBreakerFallback.md) |
| `Classification: TsgcCircuitBreakerClassification` | [TsgcCircuitBreakerClassification](./TsgcCircuitBreakerClassification.md) |
| `PerEndpoint: TsgcCircuitBreakerEndpointList` | [TsgcCircuitBreakerEndpointList](./TsgcCircuitBreakerEndpointList.md) |
| `Metrics: TsgcCircuitBreakerMetrics (read-only)` | [TsgcCircuitBreakerMetrics](./TsgcCircuitBreakerMetrics.md) |
| `Version: String (read-only)` | `String` |

## Events

| Delphi | Type |
| --- | --- |
| `OnStateChange: TsgcCircuitBreakerOnStateChange` | [TsgcCircuitBreakerOnStateChange](./TsgcCircuitBreakerOnStateChange.md) |
| `OnCallRejected: TsgcCircuitBreakerOnCallRejected` | [TsgcCircuitBreakerOnCallRejected](./TsgcCircuitBreakerOnCallRejected.md) |
| `OnFallback: TsgcCircuitBreakerOnFallback` | [TsgcCircuitBreakerOnFallback](./TsgcCircuitBreakerOnFallback.md) |
| `OnFailureRecorded: TsgcCircuitBreakerOnFailureRecorded` | [TsgcCircuitBreakerOnFailureRecorded](./TsgcCircuitBreakerOnFailureRecorded.md) |
| `OnSlowCall: TsgcCircuitBreakerOnSlowCall` | [TsgcCircuitBreakerOnSlowCall](./TsgcCircuitBreakerOnSlowCall.md) |

## Methods

```pascal
function Execute(const aKey: string; aAction: TProc): Boolean;
function ExecuteWithResult(const aKey: string; aAction: TFunc<TObject>; out aResult: TObject): Boolean;
procedure RecordSuccess(const aKey: string);
procedure RecordFailure(const aKey: string; const aException: string = '');
procedure ForceOpen(const aKey: string);
procedure ForceClose(const aKey: string);
procedure Reset(const aKey: string);
procedure ResetAll;
function GetState(const aKey: string): TsgcCircuitState;
function IsCallAllowed(const aKey: string): Boolean;
function GetFailureRate(const aKey: string): Double;
function GetTotalCalls(const aKey: string): Int64;
function GetLastStateChange(const aKey: string): TDateTime;
function GetOpenBreakers: TsgcCircuitBreakerKeyArray;
procedure SaveStateToFile(const aFileName: string);
procedure LoadStateFromFile(const aFileName: string);
function IsConnectionAllowed(const aIP: string): Boolean;
function IsMessageAllowed(const aIP: string; const aMessage: string = ''): Boolean;
procedure RegisterConnection(const aIP: string);
procedure UnregisterConnection(const aIP: string);
procedure RecordMessageError(const aIP: string; const aException: string = '');
procedure RecordMessageSuccess(const aIP: string);
```

