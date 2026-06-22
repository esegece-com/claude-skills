# TIdPOP3ServerStatEvent

kind: event handler type
unit: IdPOP3Server

A handler assigned to this event must match this signature:

```pascal
procedure(aCmd: TIdCommand; out oCount: integer; out oSize: Int64) of object
```

