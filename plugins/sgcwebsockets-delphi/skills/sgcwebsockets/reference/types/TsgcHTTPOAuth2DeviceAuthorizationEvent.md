# TsgcHTTPOAuth2DeviceAuthorizationEvent

kind: event handler type
unit: sgcHTTP_OAuth2_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; Connection: TsgcWSConnection; const ClientId, Scope: String; var Authorized: Boolean) of object
```

