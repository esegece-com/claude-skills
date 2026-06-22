# TsgcGRPCServiceConfig

kind: class
unit: sgcGRPC_ServiceConfig

## Properties

| Delphi | Type |
| --- | --- |
| `LoadBalancingPolicy: string` | `string` |

## Methods

```pascal
procedure Clear;
procedure LoadFromJSON(const aJSON: string);
function FindMethodConfig(const aService, aMethod: string) : TsgcGRPCMethodConfig;
function MethodConfigCount: Integer;
function GetMethodConfig(aIndex: Integer): TsgcGRPCMethodConfig;
```

