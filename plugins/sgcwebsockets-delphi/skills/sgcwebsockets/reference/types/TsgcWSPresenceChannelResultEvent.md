# TsgcWSPresenceChannelResultEvent

kind: event handler type
unit: sgcWebSocket_Protocol_Presence_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; const aMember: TsgcWSPresenceMember; const aChannel: TsgcWSPresenceChannel; Accept: Boolean; const aError: TsgcWSPresenceError) of object
```

