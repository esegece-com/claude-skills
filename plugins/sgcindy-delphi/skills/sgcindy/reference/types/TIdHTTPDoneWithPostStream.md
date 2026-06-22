# TIdHTTPDoneWithPostStream

kind: event handler type
unit: IdCustomHTTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdContext; ARequestInfo: TIdHTTPRequestInfo; var VCanFree: Boolean) of object
```

