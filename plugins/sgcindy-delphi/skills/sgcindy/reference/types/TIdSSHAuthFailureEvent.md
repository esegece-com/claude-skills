# TIdSSHAuthFailureEvent

kind: event handler type
unit: IdSSHClient

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aPartialSuccess: Boolean; const aAllowedMethods: string) of object
```

