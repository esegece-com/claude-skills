# TsgcHTTP2ClientAuthorizationEvent

kind: event handler type
unit: sgcHTTP2_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const Connection: TsgcHTTP2ConnectionClient; const AuthType, AuthData: String; var UserName, Password, Token: String; var Handled: Boolean) of object
```

