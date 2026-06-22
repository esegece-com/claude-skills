# TsgcWSUnknownAuthenticationEvent

kind: event handler type
unit: sgcWebSocket_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; AuthType, AuthData: String; var aUser, aPassword: String; var Authenticated: Boolean) of object
```

