# TsgcWSPresenceBeforeNewChannel

kind: event handler type
unit: sgcWebSocket_Protocol_Presence_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; const aChannel: TsgcWSPresenceChannel; const aMember: TsgcWSPresenceMember; var Accept: Boolean) of object
```

