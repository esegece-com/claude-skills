# TsgcAMQPChallengeEvent

kind: event handler type
unit: sgcAMQP

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aChallenge: String; var Challenge: String) of object
```

