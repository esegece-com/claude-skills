# TsgcHTTP2ClientResponseFragmentEvent

kind: event handler type
unit: sgcHTTP2_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const Connection: TsgcHTTP2ConnectionClient; const Request: TsgcHTTP2RequestProperty; const Fragment: TsgcHTTP2ResponseFragmentProperty) of object
```

