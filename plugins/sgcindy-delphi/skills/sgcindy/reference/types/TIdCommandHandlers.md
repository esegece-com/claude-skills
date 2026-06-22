# TIdCommandHandlers

kind: class
unit: IdCommandHandlers

## Properties

| Delphi | Type |
| --- | --- |
| `Base: TIdComponent (read-only)` | [TIdComponent](./TIdComponent.md) |
| `Items[AIndex[AIndex: Integer]: TIdCommandHandler` | [TIdCommandHandler](./TIdCommandHandler.md) |
| `ParseParamsDefault: Boolean` | `Boolean` |
| `PerformReplies: Boolean` | `Boolean` |
| `ReplyClass: TIdReplyClass (read-only)` | [TIdReplyClass](./TIdReplyClass.md) |
| `ReplyTexts: TIdReplies (read-only)` | [TIdReplies](./TIdReplies.md) |

## Events

| Delphi | Type |
| --- | --- |
| `OnAfterCommandHandler: TIdAfterCommandHandlerEvent` | [TIdAfterCommandHandlerEvent](./TIdAfterCommandHandlerEvent.md) |
| `OnBeforeCommandHandler: TIdBeforeCommandHandlerEvent` | [TIdBeforeCommandHandlerEvent](./TIdBeforeCommandHandlerEvent.md) |
| `OnCommandHandlersException: TIdCommandHandlersExceptionEvent` | [TIdCommandHandlersExceptionEvent](./TIdCommandHandlersExceptionEvent.md) |

## Methods

```pascal
function Add: TIdCommandHandler;
function HandleCommand(AContext: TIdContext; var VCommand: string): Boolean;
```

