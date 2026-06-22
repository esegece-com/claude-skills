# TsgcRCONAuthenticateEvent

kind: event handler type
unit: sgcLib_RCON_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; Authenticated: Boolean; const aPacket: TsgcRCON_Packet) of object
```

