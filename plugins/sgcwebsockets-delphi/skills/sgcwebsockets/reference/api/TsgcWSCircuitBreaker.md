# TsgcWSCircuitBreaker

unit: sgcWebSocket_CircuitBreaker
Edition: Professional

Add `sgcWebSocket_CircuitBreaker` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Enabled: Boolean` | `Boolean` | `__property bool Enabled;` |
| `DefaultKey: string` | `string` | `__property UnicodeString DefaultKey;` |
| `ServerKey: string` | `string` | `__property UnicodeString ServerKey;` |
| `Thresholds: TsgcCircuitBreakerThresholds` | [TsgcCircuitBreakerThresholds](../types/TsgcCircuitBreakerThresholds.md) | `__property TsgcCircuitBreakerThresholds * Thresholds;` |
| `TimeWindow: TsgcCircuitBreakerWindow` | [TsgcCircuitBreakerWindow](../types/TsgcCircuitBreakerWindow.md) | `__property TsgcCircuitBreakerWindow * TimeWindow;` |
| `Recovery: TsgcCircuitBreakerRecovery` | [TsgcCircuitBreakerRecovery](../types/TsgcCircuitBreakerRecovery.md) | `__property TsgcCircuitBreakerRecovery * Recovery;` |
| `Fallback: TsgcCircuitBreakerFallback` | [TsgcCircuitBreakerFallback](../types/TsgcCircuitBreakerFallback.md) | `__property TsgcCircuitBreakerFallback * Fallback;` |
| `Classification: TsgcCircuitBreakerClassification` | [TsgcCircuitBreakerClassification](../types/TsgcCircuitBreakerClassification.md) | `__property TsgcCircuitBreakerClassification * Classification;` |
| `PerEndpoint: TsgcCircuitBreakerEndpointList` | [TsgcCircuitBreakerEndpointList](../types/TsgcCircuitBreakerEndpointList.md) | `__property TsgcCircuitBreakerEndpointList * PerEndpoint;` |
| `Metrics: TsgcCircuitBreakerMetrics (read-only)` | [TsgcCircuitBreakerMetrics](../types/TsgcCircuitBreakerMetrics.md) | `__property TsgcCircuitBreakerMetrics * Metrics /* read-only */;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnStateChange: TsgcCircuitBreakerOnStateChange` | [TsgcCircuitBreakerOnStateChange](../types/TsgcCircuitBreakerOnStateChange.md) | `__property TsgcCircuitBreakerOnStateChange * OnStateChange;` |
| `OnCallRejected: TsgcCircuitBreakerOnCallRejected` | [TsgcCircuitBreakerOnCallRejected](../types/TsgcCircuitBreakerOnCallRejected.md) | `__property TsgcCircuitBreakerOnCallRejected * OnCallRejected;` |
| `OnFallback: TsgcCircuitBreakerOnFallback` | [TsgcCircuitBreakerOnFallback](../types/TsgcCircuitBreakerOnFallback.md) | `__property TsgcCircuitBreakerOnFallback * OnFallback;` |
| `OnFailureRecorded: TsgcCircuitBreakerOnFailureRecorded` | [TsgcCircuitBreakerOnFailureRecorded](../types/TsgcCircuitBreakerOnFailureRecorded.md) | `__property TsgcCircuitBreakerOnFailureRecorded * OnFailureRecorded;` |
| `OnSlowCall: TsgcCircuitBreakerOnSlowCall` | [TsgcCircuitBreakerOnSlowCall](../types/TsgcCircuitBreakerOnSlowCall.md) | `__property TsgcCircuitBreakerOnSlowCall * OnSlowCall;` |

## Methods

Delphi

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

C++Builder

```cpp
bool __fastcall Execute(const UnicodeString aKey, TProc * aAction);
bool __fastcall ExecuteWithResult(const UnicodeString aKey, TFunc<TObject> * aAction, TObject * &aResult);
void __fastcall RecordSuccess(const UnicodeString aKey);
void __fastcall RecordFailure(const UnicodeString aKey, const UnicodeString aException = '');
void __fastcall ForceOpen(const UnicodeString aKey);
void __fastcall ForceClose(const UnicodeString aKey);
void __fastcall Reset(const UnicodeString aKey);
void __fastcall ResetAll();
TsgcCircuitState * __fastcall GetState(const UnicodeString aKey);
bool __fastcall IsCallAllowed(const UnicodeString aKey);
double __fastcall GetFailureRate(const UnicodeString aKey);
long long __fastcall GetTotalCalls(const UnicodeString aKey);
System::TDateTime __fastcall GetLastStateChange(const UnicodeString aKey);
TsgcCircuitBreakerKeyArray * __fastcall GetOpenBreakers();
void __fastcall SaveStateToFile(const UnicodeString aFileName);
void __fastcall LoadStateFromFile(const UnicodeString aFileName);
bool __fastcall IsConnectionAllowed(const UnicodeString aIP);
bool __fastcall IsMessageAllowed(const UnicodeString aIP, const UnicodeString aMessage = '');
void __fastcall RegisterConnection(const UnicodeString aIP);
void __fastcall UnregisterConnection(const UnicodeString aIP);
void __fastcall RecordMessageError(const UnicodeString aIP, const UnicodeString aException = '');
void __fastcall RecordMessageSuccess(const UnicodeString aIP);
```

