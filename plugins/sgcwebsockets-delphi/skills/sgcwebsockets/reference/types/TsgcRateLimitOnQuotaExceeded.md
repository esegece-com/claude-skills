# TsgcRateLimitOnQuotaExceeded

kind: event handler type
unit: sgcWebSocket_Server_RateLimiter

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aKey, aQuotaName: string) of object
```

