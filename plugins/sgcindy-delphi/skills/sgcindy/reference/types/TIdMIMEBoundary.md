# TIdMIMEBoundary

kind: class
unit: IdMessage

## Properties

| Delphi | Type |
| --- | --- |
| `Boundary: string (read-only)` | `string` |
| `ParentPart: integer (read-only)` | `integer` |

## Methods

```pascal
procedure Push(ABoundary: string; AParentPart: integer);
procedure Pop;
procedure Clear;
function Count: integer;
```

