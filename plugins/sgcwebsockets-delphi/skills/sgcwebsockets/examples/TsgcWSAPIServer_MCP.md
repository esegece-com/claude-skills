# TsgcWSAPIServer_MCP - Example

Usage of `TsgcWSAPIServer_MCP` extracted from the **15.AI/03.MCP/01.MCP_Server** demo. See the full project for context.

API reference: [TsgcWSAPIServer_MCP](../reference/api/TsgcWSAPIServer_MCP.md)
Source demo: `15.AI/03.MCP/01.MCP_Server` (file `FMCP_Server.pas`)

```pascal
FStdioServer.MCPServer.OnMCPRequestTool := FLogic.OnRequestTool;
FStdioServer.MCPServer.OnMCPRequestPrompt := FLogic.OnRequestPrompt;
FStdioServer.MCPServer.OnMCPRequestResource := FLogic.OnRequestResource;
MCPServer.EndpointOptions.Endpoint := txtMCPEndpoint.Text;
MCPServer.MCPOptions.AuthenticationOptions.CustomHeader.Enabled :=
MCPServer.MCPOptions.AuthenticationOptions.CustomHeader.Header :=
MCPServer.MCPOptions.AuthenticationOptions.CustomHeader.Value :=
MCPServer.MCPOptions.AuthenticationOptions.ApiKey.Enabled :=
MCPServer.MCPOptions.AuthenticationOptions.ApiKey.Value :=
```

