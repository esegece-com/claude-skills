# TsgcWSHTTPBeforeCreatePostStream

kind: event handler type
unit: sgcWebSocket_Server_Base

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const Connection: TsgcWSConnection; const aHeaders: TStrings; var Accept: Boolean) of object
```

