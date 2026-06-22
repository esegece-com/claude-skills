# TsgcHTMXMessageEvent

kind: event handler type
unit: sgcHTMX_Engine_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aConnection: TsgcWSConnection; const aMessage: string; var aResponse: string) of object
```

