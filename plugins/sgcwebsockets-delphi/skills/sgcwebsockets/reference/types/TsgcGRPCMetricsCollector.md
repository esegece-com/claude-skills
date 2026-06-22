# TsgcGRPCMetricsCollector

kind: class
unit: sgcGRPC_OpenTelemetry

## Properties

| Delphi | Type |
| --- | --- |
| `Enabled: Boolean` | `Boolean` |
| `TotalCalls: Int64 (read-only)` | `Int64` |
| `TotalFailedCalls: Int64 (read-only)` | `Int64` |

## Events

| Delphi | Type |
| --- | --- |
| `OnCallCompleted: TsgcGRPCCallCompletedEvent` | [TsgcGRPCCallCompletedEvent](./TsgcGRPCCallCompletedEvent.md) |

## Methods

```pascal
procedure RecordCall(const aMetrics: TsgcGRPCCallMetrics);
procedure Clear;
function GetMethodStats(const aService, aMethod: string) : TsgcGRPCMethodStats;
function MethodStatsCount: Integer;
function GetMethodStatsByIndex(aIndex: Integer): TsgcGRPCMethodStats;
function GetTotalAverageDurationMs: Double;
function GetOverallSuccessRate: Double;
```

