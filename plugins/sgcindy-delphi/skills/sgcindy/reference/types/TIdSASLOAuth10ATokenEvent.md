# TIdSASLOAuth10ATokenEvent

kind: event handler type
unit: IdSASLOAuth

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; var ARealm, AConsumerKey, AAccessToken, ASignatureMethod, ATimestamp, ANonce, ASignature: String) of object
```

