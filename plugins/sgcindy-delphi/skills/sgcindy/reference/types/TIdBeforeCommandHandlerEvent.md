# TIdBeforeCommandHandlerEvent

kind: event handler type
unit: IdCommandHandlers

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TIdCommandHandlers; var AData: string; AContext: TIdContext) of object
```

