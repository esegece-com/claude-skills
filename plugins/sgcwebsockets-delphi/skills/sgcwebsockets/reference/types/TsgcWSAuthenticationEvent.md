# TsgcWSAuthenticationEvent

kind: event handler type
unit: sgcWebSocket_Server_Base

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; aUser, aPassword: String; var Authenticated: Boolean) of object
```

