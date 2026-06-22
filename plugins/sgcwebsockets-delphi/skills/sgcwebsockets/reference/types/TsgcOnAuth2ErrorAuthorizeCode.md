# TsgcOnAuth2ErrorAuthorizeCode

kind: event handler type
unit: sgcHTTP_OAuth2_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const Error, Error_Description, Error_URI, State, RawParams: String) of object
```

