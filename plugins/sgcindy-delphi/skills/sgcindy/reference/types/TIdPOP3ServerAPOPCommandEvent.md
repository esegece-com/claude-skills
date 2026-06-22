# TIdPOP3ServerAPOPCommandEvent

kind: event handler type
unit: IdPOP3Server

A handler assigned to this event must match this signature:

```pascal
procedure (aCmd: TIdCommand; aMailboxID: String; var vUsersPassword: String) of object
```

