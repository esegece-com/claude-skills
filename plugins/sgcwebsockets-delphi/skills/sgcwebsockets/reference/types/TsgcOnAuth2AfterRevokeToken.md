# TsgcOnAuth2AfterRevokeToken

kind: event handler type
unit: sgcHTTP_OAuth2_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const Token, TokenTypeHint, RawResponse: String) of object
```

