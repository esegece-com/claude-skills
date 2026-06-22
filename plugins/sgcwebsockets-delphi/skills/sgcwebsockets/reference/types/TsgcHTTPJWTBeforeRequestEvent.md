# TsgcHTTPJWTBeforeRequestEvent

kind: event handler type
unit: sgcHTTP_JWT_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aConnection: TsgcWSConnection; aHeaders: TStringList; var Cancel: Boolean) of object
```

