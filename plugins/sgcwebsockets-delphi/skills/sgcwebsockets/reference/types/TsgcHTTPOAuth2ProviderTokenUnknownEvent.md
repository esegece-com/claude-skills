# TsgcHTTPOAuth2ProviderTokenUnknownEvent

kind: event handler type
unit: sgcHTTP_OAuth2_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; Connection: TsgcWSConnection; Endpoint: string; Response: TsgcHTTPOAuth2ProviderResponse) of object
```

