# TsgcOnAuth2AfterAccessToken

kind: event handler type
unit: sgcHTTP_OAuth2_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const Access_Token, Token_Type, Expires_In, Refresh_Token, Scope, RawParams: String; var Handled: Boolean) of object
```

