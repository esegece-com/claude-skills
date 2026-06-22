# TIdOnGetStreams

kind: event handler type
unit: IdIOHandlerStream

A handler assigned to this event must match this signature:

```pascal
procedure(ASender: TIdIOHandlerStream; var VReceiveStream: TStream; var VSendStream: TStream) of object
```

