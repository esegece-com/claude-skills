# TsgcGRPCCallCompletedEvent

kind: event handler type
unit: sgcGRPC_OpenTelemetry

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aMetrics: TsgcGRPCCallMetrics) of object
```

