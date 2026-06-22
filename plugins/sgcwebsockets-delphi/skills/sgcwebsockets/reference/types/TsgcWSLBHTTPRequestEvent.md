# TsgcWSLBHTTPRequestEvent

kind: event handler type
unit: sgcWebSocket_LoadBalancer_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; Connection: TsgcWSConnection; ARequestInfo: TIdHTTPRequestInfo; aForward: TsgcWSServerForwardHTTP) of object
```

