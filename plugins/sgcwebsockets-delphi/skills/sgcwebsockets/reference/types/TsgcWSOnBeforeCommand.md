# TsgcWSOnBeforeCommand

kind: event handler type
unit: sgcWebSocket_Server

A handler assigned to this event must match this signature:

```pascal
procedure(const aConnection: TsgcWSConnection; ARequestInfo: TIdHTTPRequestInfo; AResponseInfo: TIdHTTPResponseInfo; var aOptions: TsgcHTTPCommandOptions) of object
```

