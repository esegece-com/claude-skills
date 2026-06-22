# TIdHTTPHeadersAvailableEvent

kind: event handler type
unit: IdCustomHTTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdContext; const AUri: string; AHeaders: TIdHeaderList; var VContinueProcessing: Boolean) of object
```

