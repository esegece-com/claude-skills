# TIdHTTPInvalidSessionEvent

kind: event handler type
unit: sgcIdCustomHTTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdContext; ARequestInfo: TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo; var VContinueProcessing: Boolean; const AInvalidSessionID: String) of object
```

