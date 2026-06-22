# TIPMCastReadEvent

kind: event handler type
unit: IdIPMCastClient

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const AData: TIdBytes; ABinding: TIdSocketHandle) of object
```

