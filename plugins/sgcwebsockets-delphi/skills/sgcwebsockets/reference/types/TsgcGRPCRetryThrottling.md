# TsgcGRPCRetryThrottling

kind: class
unit: sgcGRPC_Retry

## Properties

| Delphi | Type |
| --- | --- |
| `MaxTokens: Integer` | `Integer` |
| `TokenRatio: Double` | `Double` |

## Methods

```pascal
procedure Assign(aSource: TPersistent);
function AllowRetry: Boolean;
procedure OnSuccess;
procedure OnFailure;
```

