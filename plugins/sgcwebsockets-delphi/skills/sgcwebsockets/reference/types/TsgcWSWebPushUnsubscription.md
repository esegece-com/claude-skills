# TsgcWSWebPushUnsubscription

kind: event handler type
unit: sgcWebSocket_Server_API_WebPush

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; aSubscription: TsgcHTTP_API_WebPush_PushSubscription; var ResponseCode: Integer) of object
```

