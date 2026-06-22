# TsgcHTTPOAuth2ProviderTokenValidEvent

kind: event handler type
unit: sgcHTTP_OAuth2_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; Connection: TsgcWSConnection; Token: TsgcHTTPOAuth2ProviderToken; Response: TsgcHTTPOAuth2ProviderResponse) of object
```

