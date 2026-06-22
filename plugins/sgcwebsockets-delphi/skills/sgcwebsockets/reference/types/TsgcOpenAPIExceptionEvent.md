# TsgcOpenAPIExceptionEvent

kind: event handler type
unit: sgcHTTP_OpenAPI_Server_Engine

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; E: Exception; var aResponseCode: Integer) of object
```

