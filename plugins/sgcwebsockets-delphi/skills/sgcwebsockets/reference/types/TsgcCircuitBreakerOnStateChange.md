# TsgcCircuitBreakerOnStateChange

kind: event handler type
unit: sgcWebSocket_CircuitBreaker

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aKey: string; aOldState, aNewState: TsgcCircuitState) of object
```

