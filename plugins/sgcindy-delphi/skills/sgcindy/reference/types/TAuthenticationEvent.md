# TAuthenticationEvent

kind: event handler type
unit: IdTelnetServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdContext; const AUsername, APassword: string; var AAuthenticated: Boolean) of object
```

