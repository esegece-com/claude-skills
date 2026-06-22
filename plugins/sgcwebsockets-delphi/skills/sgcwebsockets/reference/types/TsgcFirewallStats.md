# TsgcFirewallStats

kind: class
unit: sgcWebSocket_Server_Firewall

## Properties

| Delphi | Type |
| --- | --- |
| `TotalConnections: Int64 (read-only)` | `Int64` |
| `TotalBlocked: Int64 (read-only)` | `Int64` |
| `TotalMessages: Int64 (read-only)` | `Int64` |
| `TotalViolations: Int64 (read-only)` | `Int64` |
| `ActiveConnections: Integer (read-only)` | `Integer` |

## Methods

```pascal
procedure IncrementConnections;
procedure DecrementConnections;
procedure IncrementBlocked;
procedure IncrementMessages;
procedure IncrementViolation(aType: TsgcFirewallViolationType);
procedure Reset;
function GetViolationCount(aType: TsgcFirewallViolationType): Int64;
```

