# TIdSSHHostKeyEvent

kind: event handler type
unit: IdSSHClient

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aHostKeyType: string; const aFingerprint: string; var aAction: TIdSSHHostKeyVerification) of object
```

