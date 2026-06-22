# TsgcWSFileEvent

kind: event handler type
unit: sgcWebSocket_Protocol_Files_Message

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; const aMessage: TsgcWSMessageFile) of object
```

