# TsgcWSBitfinexSubscribedEvent

kind: event handler type
unit: sgcWebSocket_API_Bitfinex

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; Channel: String; ChanId: Integer; Symbol, Pair, Key: String) of object
```

