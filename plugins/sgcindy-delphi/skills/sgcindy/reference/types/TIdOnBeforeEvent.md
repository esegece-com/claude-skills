# TIdOnBeforeEvent

kind: event handler type
unit: IdSocksServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdSocksServerContext; var VHost: string; var VPort: TIdPort; var VAllowed: Boolean) of object
```

