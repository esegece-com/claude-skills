# TIdChainEngine

kind: class
unit: IdIOHandlerChain

## Properties

| Delphi | Type |
| --- | --- |
| `Version: string (read-only)` | `string` |

## Methods

```pascal
procedure AddWork(AWorkOpUnit: TIdWorkOpUnit);
procedure BeforeDestruction;
procedure RemoveSocket(AIOHandler: TIdIOHandlerChain);
procedure SocketAccepted(AIOHandler: TIdIOHandlerChain);
procedure RemoveFreeNotification(AComponent: TComponent);
```

