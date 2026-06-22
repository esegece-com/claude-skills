# TIdHTTPCommandError

kind: event handler type
unit: IdCustomHTTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdContext; ARequestInfo: TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo; AException: Exception) of object
```

