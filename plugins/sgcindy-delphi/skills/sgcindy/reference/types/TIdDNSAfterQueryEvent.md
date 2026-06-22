# TIdDNSAfterQueryEvent

kind: event handler type
unit: IdDNSServer

A handler assigned to this event must match this signature:

```pascal
procedure(ABinding: TIdSocketHandle; ADNSHeader: TDNSHeader; var QueryResult: TIdBytes; var ResultCode: string; Query : TIdBytes) of object
```

