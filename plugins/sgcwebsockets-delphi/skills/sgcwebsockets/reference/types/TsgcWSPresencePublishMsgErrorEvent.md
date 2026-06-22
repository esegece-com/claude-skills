# TsgcWSPresencePublishMsgErrorEvent

kind: event handler type
unit: sgcWebSocket_Protocol_Presence_Message

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; const aError: TsgcWSPresenceError; const aMsg: TsgcWSPresenceMsg; const aChannel: TsgcWSPresenceChannel; const aMember: TsgcWSPresenceMember) of object
```

