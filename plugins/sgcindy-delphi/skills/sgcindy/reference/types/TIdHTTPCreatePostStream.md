# TIdHTTPCreatePostStream

kind: event handler type
unit: IdCustomHTTPServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdContext; AHeaders: TIdHeaderList; var VPostStream: TStream) of object
```

