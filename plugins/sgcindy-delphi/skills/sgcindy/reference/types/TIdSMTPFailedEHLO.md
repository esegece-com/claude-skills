# TIdSMTPFailedEHLO

kind: event handler type
unit: IdSMTPBase

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const ACode, AText: String; var VContinue: Boolean) of object
```

