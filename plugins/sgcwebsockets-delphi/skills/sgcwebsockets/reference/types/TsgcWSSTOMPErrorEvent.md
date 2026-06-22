# TsgcWSSTOMPErrorEvent

kind: event handler type
unit: sgcWebSocket_Protocol_STOMP_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; MessageText, ContentType: String; ContentLength: Integer; ReceiptId, RawHeaders: String) of object
```

