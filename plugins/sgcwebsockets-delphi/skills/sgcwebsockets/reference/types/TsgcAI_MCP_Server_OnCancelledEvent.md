# TsgcAI_MCP_Server_OnCancelledEvent

kind: event handler type
unit: sgcAI_MCP_Server

A handler assigned to this event must match this signature:

```pascal
procedure(Sender: TObject; const aSession: TsgcAI_MCP_Session; const aNotification: TsgcAI_MCP_Notification_Cancelled) of object
```

