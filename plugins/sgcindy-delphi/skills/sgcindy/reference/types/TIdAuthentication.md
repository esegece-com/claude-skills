# TIdAuthentication

kind: class
unit: IdAuthentication

## Properties

| Delphi | Type |
| --- | --- |
| `AuthParams: TIdHeaderList` | `TIdHeaderList` |
| `Params: TIdHeaderList (read-only)` | `TIdHeaderList` |
| `Username: String` | `String` |
| `Password: String` | `String` |
| `Steps: Integer (read-only)` | `Integer` |
| `CurrentStep: Integer (read-only)` | `Integer` |

## Methods

```pascal
procedure Reset;
procedure SetRequest(const AMethod, AUri: String);
function Authentication: String;
function KeepAlive: Boolean;
function Next: TIdAuthWhatsNext;
```

