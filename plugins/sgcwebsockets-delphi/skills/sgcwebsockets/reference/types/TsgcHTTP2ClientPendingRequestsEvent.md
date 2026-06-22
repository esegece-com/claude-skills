# TsgcHTTP2ClientPendingRequestsEvent

kind: event handler type
unit: sgcHTTP2_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const Connection: TsgcHTTP2ConnectionClient; var aReconnect, aClear: Boolean) of object
```

