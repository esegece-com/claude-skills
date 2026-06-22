# TsgcWSAPIClient_MCP - Example

Usage of `TsgcWSAPIClient_MCP` extracted from the **15.AI/03.MCP/02.MCP_Client** demo. See the full project for context.

API reference: [TsgcWSAPIClient_MCP](../reference/api/TsgcWSAPIClient_MCP.md)
Source demo: `15.AI/03.MCP/02.MCP_Client` (file `uMCPClient.pas`)

```pascal
procedure TFRMMCPClient.btnInitializeClick(Sender: TObject);
  begin
  if rgTransport.ItemIndex = 1 then
  begin
  MCP.MCPOptions.Transport := aimcptrStdio;
  MCP.MCPOptions.StdioOptions.Command := txtStdioCommand.Text;
  MCP.MCPOptions.StdioOptions.Arguments := '';
  end
  else
  begin
  MCP.MCPOptions.Transport := aimcptrHttp;
  MCP.MCPOptions.HttpOptions.URL := txtURL.Text;
  end;
  
  MCP.MCPOptions.ClientInfo.Name := txtClientInfoName.Text;
  MCP.MCPOptions.ClientInfo.Title := txtClientInfoTitle.Text;
  MCP.MCPOptions.ClientInfo.Version := txtClientInfoVersion.Text;
  
  MCP.MCPOptions.AuthenticationOptions.CustomHeader.Enabled :=
  chkAuthCustomHeader.Checked;
  MCP.MCPOptions.AuthenticationOptions.CustomHeader.Header :=
  txtCustomHeader.Text;
  MCP.MCPOptions.AuthenticationOptions.CustomHeader.Value :=
  txtCustomHeaderValue.Text;
  MCP.MCPOptions.AuthenticationOptions.ApiKey.Enabled := chkAuthApiKey.Checked;
  MCP.MCPOptions.AuthenticationOptions.ApiKey.Value := txtApiKeyValue.Text;
  
  MCP.Initialize;
  end;

procedure TFRMMCPClient.btnListPromptsClick(Sender: TObject);
  begin
  MCP.ListPrompts;
  end;

procedure TFRMMCPClient.btnListResourcesClick(Sender: TObject);
  begin
  MCP.ListResources;
  end;

procedure TFRMMCPClient.btnListToolsClick(Sender: TObject);
  begin
  MCP.ListTools;
  end;

procedure TFRMMCPClient.btnRequestResourceClick(Sender: TObject);
  begin
  MCP.RequestResource('file:///project/src/main.rs');
  end;

procedure TFRMMCPClient.btnRequestToolClick(Sender: TObject);
  var
  oJSON: TsgcJSON;
  begin
  oJSON := TsgcJSON.Create(nil);
  Try
  oJSON.AddPair('city', 'Barcelona');
  MCP.RequestTool('GetTemperature', oJSON)
  Finally
  oJSON.Free;
```

