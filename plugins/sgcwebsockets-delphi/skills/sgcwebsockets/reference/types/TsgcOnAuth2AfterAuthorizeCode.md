# TsgcOnAuth2AfterAuthorizeCode

kind: event handler type
unit: sgcHTTP_OAuth2_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const Code, State, Scope, RawParams: String; var Handled: Boolean) of object
```

