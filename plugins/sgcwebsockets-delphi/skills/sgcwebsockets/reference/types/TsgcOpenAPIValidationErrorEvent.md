# TsgcOpenAPIValidationErrorEvent

kind: event handler type
unit: sgcHTTP_OpenAPI_Server_Engine

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aOperationId: string; const aErrors: TStringList; const aContext: TsgcOpenAPIServerContext; var Continue: Boolean) of object
```

