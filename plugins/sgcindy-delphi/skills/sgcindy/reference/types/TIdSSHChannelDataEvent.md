# TIdSSHChannelDataEvent

kind: event handler type
unit: IdSSHClient

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aChannelId: Cardinal; const aData: TIdBytes) of object
```

