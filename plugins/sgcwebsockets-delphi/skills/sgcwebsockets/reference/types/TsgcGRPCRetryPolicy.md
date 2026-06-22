# TsgcGRPCRetryPolicy

kind: class
unit: sgcGRPC_Retry

## Properties

| Delphi | Type |
| --- | --- |
| `Enabled: Boolean` | `Boolean` |
| `MaxAttempts: Integer` | `Integer` |
| `InitialBackoff: Integer` | `Integer` |
| `MaxBackoff: Integer` | `Integer` |
| `BackoffMultiplier: Double` | `Double` |
| `RetryableStatusCodes: TsgcGRPCStatusCodes` | `TsgcGRPCStatusCodes` |
| `Throttling: TsgcGRPCRetryThrottling` | [TsgcGRPCRetryThrottling](./TsgcGRPCRetryThrottling.md) |

## Methods

```pascal
procedure Assign(aSource: TPersistent);
function IsRetryableStatus(aCode: TsgcGRPCStatusCode): Boolean;
function CalculateBackoff(aAttempt: Integer): Integer;
```

