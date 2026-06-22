# TsgcHTTPOAuth2AfterRevokeTokenEvent

kind: event handler type
unit: sgcHTTP_OAuth2_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; Connection: TsgcWSConnection; const Token, TokenTypeHint: String; var Revoked: Boolean) of object
```

