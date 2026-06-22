# TsgcOnWhatsAppClientMessageReceived

kind: event handler type
unit: sgcLib_WhatsApp_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aMessage: TsgcWhatsApp_Receive_Message; var aMarkAsRead: Boolean) of object
```

