# TsgcHTTPOAuth2AfterIntrospectTokenEvent

kind: event handler type
unit: sgcHTTP_OAuth2_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; Connection: TsgcWSConnection; OAuth2: TsgcHTTPOAuth2Request; const Token: String; var IsActive: Boolean) of object
```

