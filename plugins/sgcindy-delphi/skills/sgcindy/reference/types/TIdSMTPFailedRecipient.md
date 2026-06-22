# TIdSMTPFailedRecipient

kind: event handler type
unit: IdSMTPBase

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const AAddress, ACode, AText: String; var VContinue: Boolean) of object
```

