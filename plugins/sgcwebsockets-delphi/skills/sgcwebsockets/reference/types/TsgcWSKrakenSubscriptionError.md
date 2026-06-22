# TsgcWSKrakenSubscriptionError

kind: event handler type
unit: sgcWebSocket_API_Kraken

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; ErrorMessage: String; Pair: String; Subscription: String; ReqID: Integer) of object
```

