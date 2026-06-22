# TsgcWSKrakenUnSubscribedEvent

kind: event handler type
unit: sgcWebSocket_API_Kraken

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; ChannelId: Integer; Pair, Subscription: String; ReqID: Integer) of object
```

