# TsgcOpenAPIAuthenticateEvent

kind: event handler type
unit: sgcHTTP_OpenAPI_Server_Engine

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aOperationId: string; const aContext: TsgcOpenAPIServerContext; var Authenticated: Boolean) of object
```

