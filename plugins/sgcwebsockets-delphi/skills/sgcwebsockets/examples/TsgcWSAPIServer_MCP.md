# TsgcWSAPIServer_MCP - Example

Full source of `FMCP_Server.pas` from the **15.AI/03.MCP/01.MCP_Server** demo, which uses `TsgcWSAPIServer_MCP`.

API reference: [TsgcWSAPIServer_MCP](../reference/api/TsgcWSAPIServer_MCP.md)
Source demo: `15.AI/03.MCP/01.MCP_Server` (file `FMCP_Server.pas`)

```pascal
unit FMCP_Server;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics, Controls, Forms,
  Dialogs, StdCtrls, ExtCtrls, StrUtils, Math,
  // sgc
  sgcBase_Classes, sgcTCP_Classes, sgcWebSocket_Classes, sgcWebSocket_Types,
  sgcWebSocket_Classes_Indy, sgcWebSocket_Server, sgcWebSocket,
  sgcIdCustomHTTPServer, sgcSocket_Classes, sgcHTTP_Classes, sgcHTTP,
  sgcWebSocket_Server_API_MCP, sgcWebSocket_Server_APIs,
  sgcAI_MCP_Classes, sgcAI_MCP_Types, sgcAI,
  uMCPServerLogic, sgcAI_MCP_Server;

type
  TFRMMCPServer = class(TForm)
    btnStart: TButton;
    btnStop: TButton;
    Label1: TLabel;
    Label2: TLabel;
    txtHost: TEdit;
    Label3: TLabel;
    Default: TLabel;
    txtDefaultPort: TEdit;
    pnlLeft: TPanel;
    pnlOptions: TPanel;
    memoLog: TMemo;
    Server: TsgcWebSocketHTTPServer;
    MCPServer: TsgcWSAPIServer_MCP;
    Label4: TLabel;
    txtMCPEndpoint: TEdit;
    pnlTop: TPanel;
    Label5: TLabel;
    chkAuthCustomHeader: TCheckBox;
    txtCustomHeader: TEdit;
    txtCustomHeaderValue: TEdit;
    Label6: TLabel;
    Label7: TLabel;
    chkAuthApiKey: TCheckBox;
    txtApiKeyValue: TEdit;
    rgTransport: TRadioGroup;
    procedure FormCreate(Sender: TObject);
    procedure btnStartClick(Sender: TObject);
    procedure btnStopClick(Sender: TObject);
    procedure MCPServerMCPHTTPRequest(Sender: TObject;
      const aRequest: TsgcHTTPRequest; const aResponse: TsgcHTTPResponse;
      var Handled: Boolean);
    procedure MCPServerMCPHTTPResponse(Sender: TObject;
      const aRequest: TsgcHTTPRequest; const aResponse: TsgcHTTPResponse);
    procedure MCPServerMCPRequestPrompt(Sender: TObject;
      const aSession: TsgcAI_MCP_Session;
      const aRequest: TsgcAI_MCP_Request_PromptsGet;
      const aResponse: TsgcAI_MCP_Response_PromptsGet);
    procedure MCPServerMCPRequestResource(Sender: TObject;
      const aSession: TsgcAI_MCP_Session;
      const aRequest: TsgcAI_MCP_Request_ResourcesRead;
      const aResponse: TsgcAI_MCP_Response_ResourcesRead);
    procedure MCPServerMCPRequestTool(Sender: TObject;
      const aSession: TsgcAI_MCP_Session;
      const aRequest: TsgcAI_MCP_Request_ToolsCall;
      const aResponse: TsgcAI_MCP_Response_ToolsCall);
    procedure MCPServerMCPSessionEnd(Sender: TObject;
      const aSession: TsgcAI_MCP_Session);
    procedure MCPServerMCPSessionNew(Sender: TObject;
      const aSession: TsgcAI_MCP_Session);
    procedure serverShutdown(Sender: TObject);
    procedure serverStartup(Sender: TObject);
  private
    FLogic: TMCPServerLogic;
    FStdioServer: TsgcAI_MCP_Server_Stdio;
    FStdioThread: TsgcMCPStdioThread;
    procedure DoLog(const aText: String);
  public
    destructor Destroy; override;
    procedure DoConfigureServer;
    procedure DoConfigureStdio;
    procedure DoConfigureMCP;
  end;

var
  FRMMCPServer: TFRMMCPServer;

implementation

uses
  sgcBase_Helpers, sgcAI_MCP_Const;

{$R *.dfm}

procedure TFRMMCPServer.FormCreate(Sender: TObject);
begin
  FLogic := TMCPServerLogic.Create;
  FLogic.OnLog := DoLog;
  Randomize;
  btnStart.Click;
end;

destructor TFRMMCPServer.Destroy;
begin
  if Assigned(FStdioThread) then
  begin
    FStdioThread.Terminate;
    FStdioThread := nil;
  end;
  if Assigned(FStdioServer) then
    FStdioServer.Free;
  if Assigned(FLogic) then
    FLogic.Free;
  inherited;
end;

procedure TFRMMCPServer.btnStartClick(Sender: TObject);
begin
  DoConfigureMCP;
  case rgTransport.ItemIndex of
    1:
      DoConfigureStdio; // stdio only
    2:
      begin
        DoConfigureServer;
        DoConfigureStdio;
      end; // both
  else
    DoConfigureServer; // 0 = HTTP only (default)
  end;
end;

procedure TFRMMCPServer.btnStopClick(Sender: TObject);
begin
  Server.Active := False;
  if Assigned(FStdioThread) then
  begin
    FStdioThread.Terminate;
    FStdioThread := nil;
  end;
end;

procedure TFRMMCPServer.DoConfigureMCP;
begin
  FLogic.RegisterMCP(MCPServer.Tools, MCPServer.Prompts, MCPServer.Resources);
end;

procedure TFRMMCPServer.DoConfigureStdio;
begin
  if not Assigned(FStdioServer) then
    FStdioServer := TsgcAI_MCP_Server_Stdio.Create(nil);
  FStdioServer.ServerInfo.Name := 'sgcWebSockets MCP Server';
  FStdioServer.ServerInfo.Version := '1.0';
  FLogic.RegisterMCP(FStdioServer.MCPServer.Tools,
    FStdioServer.MCPServer.Prompts, FStdioServer.MCPServer.Resources);
  FStdioServer.MCPServer.OnMCPRequestTool := FLogic.OnRequestTool;
  FStdioServer.MCPServer.OnMCPRequestPrompt := FLogic.OnRequestPrompt;
  FStdioServer.MCPServer.OnMCPRequestResource := FLogic.OnRequestResource;
  DoLog('#stdio MCP server running (reads stdin / writes stdout)');
  if not Assigned(FStdioThread) then
    FStdioThread := TsgcMCPStdioThread.Create(FStdioServer);
end;

procedure TFRMMCPServer.DoConfigureServer;
begin
  // ... MCP options
  MCPServer.EndpointOptions.Endpoint := txtMCPEndpoint.Text;

  // ... MCP Authentication
  MCPServer.MCPOptions.AuthenticationOptions.CustomHeader.Enabled :=
    chkAuthCustomHeader.Checked;
  MCPServer.MCPOptions.AuthenticationOptions.CustomHeader.Header :=
    txtCustomHeader.Text;
  MCPServer.MCPOptions.AuthenticationOptions.CustomHeader.Value :=
    txtCustomHeaderValue.Text;
  MCPServer.MCPOptions.AuthenticationOptions.ApiKey.Enabled :=
    chkAuthApiKey.Checked;
  MCPServer.MCPOptions.AuthenticationOptions.ApiKey.Value :=
    txtApiKeyValue.Text;

  // ... bindings
  Server.Port := StrToInt(txtDefaultPort.Text);
  Server.SSLOptions.Port := StrToInt(txtDefaultPort.Text);
  Server.SSLOptions.OpenSSL_Options.APIVersion := oslAPI_3_0;
  Server.SSLOptions.Version := tls1_3;
  Server.SSL := True;
  Server.Bindings.Clear;
  With Server.Bindings.Add do
  begin
    Port := StrToInt(txtDefaultPort.Text);
    IP := txtHost.Text;
  end;

  // ... active
  Server.Active := True;
end;

procedure TFRMMCPServer.DoLog(const aText: String);
begin
  if Assigned(memoLog) then
    memoLog.Lines.Add(aText);
end;

procedure TFRMMCPServer.MCPServerMCPHTTPRequest(Sender: TObject;
  const aRequest: TsgcHTTPRequest; const aResponse: TsgcHTTPResponse;
  var Handled: Boolean);
begin
  DoLog('#http_request: ' + aRequest.Content);
end;

procedure TFRMMCPServer.MCPServerMCPHTTPResponse(Sender: TObject;
  const aRequest: TsgcHTTPRequest; const aResponse: TsgcHTTPResponse);
begin
  DoLog('#http_response: ' + aResponse.Content);
end;

procedure TFRMMCPServer.MCPServerMCPRequestPrompt(Sender: TObject;
  const aSession: TsgcAI_MCP_Session;
  const aRequest: TsgcAI_MCP_Request_PromptsGet;
  const aResponse: TsgcAI_MCP_Response_PromptsGet);
begin
  FLogic.OnRequestPrompt(Sender, aSession, aRequest, aResponse);
end;

procedure TFRMMCPServer.MCPServerMCPRequestResource(Sender: TObject;
  const aSession: TsgcAI_MCP_Session;
  const aRequest: TsgcAI_MCP_Request_ResourcesRead;
  const aResponse: TsgcAI_MCP_Response_ResourcesRead);
begin
  FLogic.OnRequestResource(Sender, aSession, aRequest, aResponse);
end;

procedure TFRMMCPServer.MCPServerMCPRequestTool(Sender: TObject;
  const aSession: TsgcAI_MCP_Session;
  const aRequest: TsgcAI_MCP_Request_ToolsCall;
  const aResponse: TsgcAI_MCP_Response_ToolsCall);
begin
  FLogic.OnRequestTool(Sender, aSession, aRequest, aResponse);
end;

procedure TFRMMCPServer.MCPServerMCPSessionEnd(Sender: TObject;
  const aSession: TsgcAI_MCP_Session);
begin
  DoLog('#session_end: ' + aSession.Id);
end;

procedure TFRMMCPServer.MCPServerMCPSessionNew(Sender: TObject;
  const aSession: TsgcAI_MCP_Session);
begin
  DoLog('#session_new: ' + aSession.Id);
end;

procedure TFRMMCPServer.serverShutdown(Sender: TObject);
begin
  DoLog('#Server Stopped: ' + txtHost.Text + ':' + txtDefaultPort.Text);
end;

procedure TFRMMCPServer.serverStartup(Sender: TObject);
begin
  DoLog('#Server Started: ' + txtHost.Text + ':' + txtDefaultPort.Text);
end;

end.
```

