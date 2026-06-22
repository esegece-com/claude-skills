# TsgcHTTP2ClientGoAwayEvent

kind: event handler type
unit: sgcHTTP2_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const Connection: TsgcHTTP2ConnectionClient; const GoAway: TsgcHTTP2GoAwayProperty) of object
```

