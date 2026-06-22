# TIdOnVerifyEvent

kind: event handler type
unit: IdSocksServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdSocksServerContext; const AHost, APeer: string; var VAllowed: Boolean) of object
```

