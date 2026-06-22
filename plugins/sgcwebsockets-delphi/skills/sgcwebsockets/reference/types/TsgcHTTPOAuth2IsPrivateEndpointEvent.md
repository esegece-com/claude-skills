# TsgcHTTPOAuth2IsPrivateEndpointEvent

kind: event handler type
unit: sgcHTTP_OAuth2_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aEndpoint: string; var IsPrivate: Boolean) of object
```

