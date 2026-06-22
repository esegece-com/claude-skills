# TIdIRCUserEvent

kind: event handler type
unit: IdIrcServer

A handler assigned to this event must match this signature:

```pascal
procedure(AContext: TIdCommand; UserName, HostName, ServerName, RealName: string) of object
```

