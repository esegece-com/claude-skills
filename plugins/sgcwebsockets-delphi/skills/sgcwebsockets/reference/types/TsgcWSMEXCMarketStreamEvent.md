# TsgcWSMEXCMarketStreamEvent

kind: event handler type
unit: sgcWebSocket_API_MEXC

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aMessage: TsgcMEXCSpotProtoMessage; const aStream: TMemoryStream) of object
```

