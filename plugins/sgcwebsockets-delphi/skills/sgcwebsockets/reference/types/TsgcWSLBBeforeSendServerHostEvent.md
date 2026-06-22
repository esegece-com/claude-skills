# TsgcWSLBBeforeSendServerHostEvent

kind: event handler type
unit: sgcWebSocket_LoadBalancer_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; var Binding: TsgcWSLoadBalancerServerBinding) of object
```

