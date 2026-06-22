# TsgcWSPresenceGetMembersEvent

kind: event handler type
unit: sgcWebSocket_Protocol_Presence_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; const aMembers: TsgcWSPresenceMemberList; const aChannel: TsgcWSPresenceChannel) of object
```

