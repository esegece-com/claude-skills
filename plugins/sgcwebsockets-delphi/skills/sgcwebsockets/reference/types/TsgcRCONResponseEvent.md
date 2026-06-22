# TsgcRCONResponseEvent

kind: event handler type
unit: sgcLib_RCON_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aResponse: string; const aPacket: TsgcRCON_Packet) of object
```

