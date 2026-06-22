# TsgcAI_MCP_Server_OnRequestToolEvent

kind: event handler type
unit: sgcAI_MCP_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSession: TsgcAI_MCP_Session; const aRequest: TsgcAI_MCP_Request_ToolsCall; const aResponse: TsgcAI_MCP_Response_ToolsCall) of object
```

