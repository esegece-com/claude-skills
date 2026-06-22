# TsgcRateLimitStats

kind: class
unit: sgcWebSocket_Server_RateLimiter

## Properties

| Delphi | Type |
| --- | --- |
| `TotalRequests: Int64` | `Int64` |
| `TotalThrottled: Int64` | `Int64` |
| `TotalQuotaExceeded: Int64` | `Int64` |
| `ActiveKeys: Integer` | `Integer` |
| `Uptime: Int64 (read-only)` | `Int64` |

## Methods

```pascal
procedure Reset;
procedure IncrementRequests;
procedure IncrementThrottled;
procedure IncrementQuotaExceeded;
procedure SetActiveKeys(aValue: Integer);
function GetUptime: Int64;
```

