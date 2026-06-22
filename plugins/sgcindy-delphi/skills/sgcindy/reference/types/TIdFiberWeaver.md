# TIdFiberWeaver

kind: class
unit: IdFiberWeaver

## Properties

| Delphi | Type |
| --- | --- |
| `Version: string (read-only)` | `string` |

## Methods

```pascal
procedure Add( AFiber: TIdFiber );
function WaitForFibers( ATimeout: Cardinal = Infinite ): Boolean;
procedure RemoveFreeNotification(AComponent: TComponent);
```

