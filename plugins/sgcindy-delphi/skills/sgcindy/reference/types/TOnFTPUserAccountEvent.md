# TOnFTPUserAccountEvent

kind: event handler type
unit: IdFTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(ASender : TIdFTPServerContext; const AUsername, APassword,AAcount: string; var AAuthenticated: Boolean) of object
```

