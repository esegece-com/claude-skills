# TsgcHTTP2ClientStreamResponseFragmentEvent

kind: event handler type
unit: sgcHTTP2_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const Connection: TsgcHTTP2ConnectionClient; const Stream: TsgcHTTP2_StreamResponse; const Bytes: TBytes) of object
```

