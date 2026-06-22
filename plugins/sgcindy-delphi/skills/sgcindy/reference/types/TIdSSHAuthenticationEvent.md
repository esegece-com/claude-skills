# TIdSSHAuthenticationEvent

kind: event handler type
unit: IdSSHClient

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aAuthMethods: TIdSSHAuthMethods; var aMethod: TIdSSHAuthMethod; var aUsername, aPassword: string) of object
```

