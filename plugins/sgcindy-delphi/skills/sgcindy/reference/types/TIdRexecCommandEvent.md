# TIdRexecCommandEvent

kind: event handler type
unit: IdRexecServer

A handler assigned to this event must match this signature:

```pascal
procedure (AThread: TIdContext; AStdError : TIdTCPClient; AUserName, APassword, ACommand : String) of object
```

