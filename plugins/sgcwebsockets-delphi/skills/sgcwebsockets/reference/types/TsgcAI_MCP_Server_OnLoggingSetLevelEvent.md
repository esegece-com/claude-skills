# TsgcAI_MCP_Server_OnLoggingSetLevelEvent

kind: event handler type
unit: sgcAI_MCP_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSession: TsgcAI_MCP_Session; const aRequest: TsgcAI_MCP_Request_LoggingSetLevel; const aResponse: TsgcAI_MCP_Response_LoggingSetLevel) of object
```

