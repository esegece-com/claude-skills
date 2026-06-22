# TsgcWSRPCErrorEvent

kind: event handler type
unit: sgcWebSocket_Protocol_sgc_Client

A handler assigned to this event must match this signature:

```pascal
procedure(Connection: TsgcWSConnection; Id: string; ErrorCode: integer; ErrorMessage, ErrorData: string) of object
```

