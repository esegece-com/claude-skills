# TsgcHTTPOAuth2AuthenticationEvent

kind: event handler type
unit: sgcHTTP_OAuth2_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; OAuth2: TsgcHTTPOAuth2Request; aUser, aPassword: String; var Authenticated: Boolean) of object
```

