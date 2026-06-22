# TsgcWSPresenceChannelInvitationEvent

kind: event handler type
unit: sgcWebSocket_Protocol_Presence_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; const aMember: TsgcWSPresenceMember; const aChannel: TsgcWSPresenceChannel; var Accept: Boolean; var aErrorCode: integer; var aErrorText: string) of object
```

