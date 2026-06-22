# TOnFTPUserLoginEvent

kind: event handler type
unit: IdFTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TIdFTPServerContext; const AUsername, APassword: string; var AAuthenticated: Boolean) of object
```

