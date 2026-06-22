# TsgcHTTPOAuth2DeviceCodeVerificationEvent

kind: event handler type
unit: sgcHTTP_OAuth2_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; Connection: TsgcWSConnection; const UserCode: String; var Authenticated: Boolean) of object
```

