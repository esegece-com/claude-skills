# TsgcHTTP2ClientPushPromiseEvent

kind: event handler type
unit: sgcHTTP2_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const Connection: TsgcHTTP2ConnectionClient; const PushPromise: TsgcHTTP2_Frame_PushPromise; var Cancel: Boolean) of object
```

