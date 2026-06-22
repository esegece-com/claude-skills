# TIdUserManagerAuthenticationEvent

kind: event handler type
unit: IdUserAccounts

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const AUsername: String; var VPassword: String; var VUserHandle: TIdUserHandle; var VUserAccess: TIdUserAccess) of object
```

