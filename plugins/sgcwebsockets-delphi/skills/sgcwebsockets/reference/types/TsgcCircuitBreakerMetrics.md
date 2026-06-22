# TsgcCircuitBreakerMetrics

kind: class
unit: sgcWebSocket_CircuitBreaker

## Properties

| Delphi | Type |
| --- | --- |
| `TotalCalls: Int64 (read-only)` | `Int64` |
| `TotalFailures: Int64 (read-only)` | `Int64` |
| `TotalSuccesses: Int64 (read-only)` | `Int64` |
| `TotalRejected: Int64 (read-only)` | `Int64` |
| `CurrentOpenBreakers: Integer (read-only)` | `Integer` |
| `AverageLatencyMs: Double (read-only)` | `Double` |

## Methods

```pascal
procedure Assign(Source: TPersistent);
procedure Reset;
procedure IncTotalCalls;
procedure IncTotalFailures;
procedure IncTotalSuccesses;
procedure IncTotalRejected;
procedure AddLatency(aMs: Integer);
procedure SetOpenBreakers(aValue: Integer);
```

