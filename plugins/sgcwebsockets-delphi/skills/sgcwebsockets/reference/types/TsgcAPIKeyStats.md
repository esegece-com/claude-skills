# TsgcAPIKeyStats

kind: class
unit: sgcWebSocket_Server_APIKeyManager

## Properties

| Delphi | Type |
| --- | --- |
| `TotalKeys: Int64 (read-only)` | `Int64` |
| `ActiveKeys: Int64 (read-only)` | `Int64` |
| `RevokedKeys: Int64 (read-only)` | `Int64` |
| `ExpiredKeys: Int64 (read-only)` | `Int64` |
| `TotalValidations: Int64 (read-only)` | `Int64` |
| `TotalValidationFailures: Int64 (read-only)` | `Int64` |
| `LastIssuedAt: TDateTime (read-only)` | `TDateTime` |

## Methods

```pascal
procedure IncrementTotalKeys;
procedure IncrementActiveKeys;
procedure DecrementActiveKeys;
procedure IncrementRevokedKeys;
procedure IncrementExpiredKeys;
procedure IncrementValidations;
procedure IncrementValidationFailures;
procedure SetLastIssuedAt(aValue: TDateTime);
procedure Reset;
```

