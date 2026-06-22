# TOnSyslogEvent

kind: event handler type
unit: IdSysLogServer

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; ASysLogMessage: TIdSysLogMessage; ABinding: TIdSocketHandle) of object
```

