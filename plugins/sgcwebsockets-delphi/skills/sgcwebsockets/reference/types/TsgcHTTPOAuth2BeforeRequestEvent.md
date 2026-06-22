# TsgcHTTPOAuth2BeforeRequestEvent

kind: event handler type
unit: sgcHTTP_OAuth2_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aConnection: TsgcWSConnection; aHeaders: TStringList; var Cancel: Boolean) of object
```

