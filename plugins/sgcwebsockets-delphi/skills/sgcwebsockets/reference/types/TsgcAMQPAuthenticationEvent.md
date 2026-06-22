# TsgcAMQPAuthenticationEvent

kind: event handler type
unit: sgcAMQP

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aMechanisms: TsgcAMQPAuthentications; var Mechanism: TsgcAMQPAuthentication; var User, Password: string) of object
```

