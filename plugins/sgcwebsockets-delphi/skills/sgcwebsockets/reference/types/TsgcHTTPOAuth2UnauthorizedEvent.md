# TsgcHTTPOAuth2UnauthorizedEvent

kind: event handler type
unit: sgcHTTP_OAuth2_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aConnection: TsgcWSConnection; var Disconnect: Boolean) of object
```

