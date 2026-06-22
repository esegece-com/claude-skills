# TIdRSHCommandEvent

kind: event handler type
unit: IdRSHServer

A handler assigned to this event must match this signature:

```pascal
procedure (AThread: TIdContext; AStdError : TIdTCPClient; AClientUserName, AHostUserName, ACommand : String) of object
```

