# TIdSMTPRelayStatus

kind: event handler type
unit: IdSMTPRelay

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; AEMailAddress: TIdEmailAddressItem; Action: TIdSMTPRelayStatusAction) of Object
```

