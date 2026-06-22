# TsgcHTTPOAuth2ResponseErrorEvent

kind: event handler type
unit: sgcHTTP_OAuth2_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aConnection: TsgcWSConnection; var aResponseCode: Integer; var aResponseText: String; var aHeaders: TStringList) of object
```

