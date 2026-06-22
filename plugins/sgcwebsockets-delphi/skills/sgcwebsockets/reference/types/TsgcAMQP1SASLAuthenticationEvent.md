# TsgcAMQP1SASLAuthenticationEvent

kind: event handler type
unit: sgcAMQP1_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aCode: TsgcAMQP1SaslCode; const aDescription: string; var Handled: Boolean) of object
```

