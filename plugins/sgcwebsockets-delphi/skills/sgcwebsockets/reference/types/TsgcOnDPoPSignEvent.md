# TsgcOnDPoPSignEvent

kind: event handler type
unit: sgcHTTP_OAuth2_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const SigningInput, Algorithm: String; var Signature: String; var Handled: Boolean) of object
```

