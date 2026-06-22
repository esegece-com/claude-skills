# TsgcWSAPIClient_MCP - Example

Full source of `uMCPClient.pas` from the **15.AI/03.MCP/02.MCP_Client** demo, which uses `TsgcWSAPIClient_MCP`.

API reference: [TsgcWSAPIClient_MCP](../reference/api/TsgcWSAPIClient_MCP.md)
Source demo: `15.AI/03.MCP/02.MCP_Client` (file `uMCPClient.pas`)

```pascal
unit uMCPClient;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls, ExtCtrls,
  sgcBase_Classes, sgcAI_MCP_Classes, sgcAI_MCP_Client, sgcAI,
  sgcAI_MCP_Types,
  sgcSocket_Classes, sgcTCP_Classes, sgcWebSocket_Classes;

type
  TFRMMCPClient = class(TForm)
    pnlTopServer: TPanel;
    txtURL: TEdit;
    Label1: TLabel;
    MCP: TsgcWSAPIClient_MCP;
    pnlTopClient: TPanel;
    txtClientInfoName: TEdit;
    Label2: TLabel;
    txtClientInfoTitle: TEdit;
    txtClientInfoVersion: TEdit;
    Label3: TLabel;
    Label4: TLabel;
    pnlBottom: TPanel;
    btnInitialize: TButton;
    btnListTools: TButton;
    pnlBody: TPanel;
    memoLog: TMemo;
    btnRequestTool: TButton;
    btnListPrompts: TButton;
    Button2: TButton;
    btnListResources: TButton;
    btnRequestResource: TButton;
    Label5: TLabel;
    chkAuthCustomHeader: TCheckBox;
    chkAuthApiKey: TCheckBox;
    txtApiKeyValue: TEdit;
    txtCustomHeader: TEdit;
    txtCustomHeaderValue: TEdit;
    Label7: TLabel;
    Label6: TLabel;
    rgTransport: TRadioGroup;
    lblStdioCommand: TLabel;
    txtStdioCommand: TEdit;
    procedure btnInitializeClick(Sender: TObject);
    procedure btnListPromptsClick(Sender: TObject);
    procedure btnListResourcesClick(Sender: TObject);
    procedure btnListToolsClick(Sender: TObject);
    procedure btnRequestResourceClick(Sender: TObject);
    procedure btnRequestToolClick(Sender: TObject);
    procedure Button2Click(Sender: TObject);
    procedure MCPMCPInitialize(Sender: TObject;
      const aRequest: TsgcAI_MCP_Request_Initialize;
      const aResponse: TsgcAI_MCP_Response_Initialize; var Accept: Boolean);
    procedure MCPMCPListPrompts(Sender: TObject;
      const aRequest: TsgcAI_MCP_Request_PromptsList;
      const aResponse: TsgcAI_MCP_Response_PromptsList);
    procedure MCPMCPListResources(Sender: TObject;
      const aRequest: TsgcAI_MCP_Request_ResourcesList;
      const aResponse: TsgcAI_MCP_Response_ResourcesList);
    procedure MCPMCPListTools(Sender: TObject;
      const aRequest: TsgcAI_MCP_Request_ToolsList;
      const aResponse: TsgcAI_MCP_Response_ToolsList);
    procedure MCPMCPResponsePrompt(Sender: TObject;
      const aRequest: TsgcAI_MCP_Request_PromptsGet;
      const aResponse: TsgcAI_MCP_Response_PromptsGet);
    procedure MCPMCPResponseResource(Sender: TObject;
      const aRequest: TsgcAI_MCP_Request_ResourcesRead;
      const aResponse: TsgcAI_MCP_Response_ResourcesRead);
    procedure MCPMCPResponseTool(Sender: TObject;
      const aRequest: TsgcAI_MCP_Request_ToolsCall;
      const aResponse: TsgcAI_MCP_Response_ToolsCall);
    procedure MCPMCPStreamMessage(Sender: TObject; const aMessage: string;
      var Cancel: Boolean);
  private
    procedure DoLog(const aText: string);
    { Private declarations }
  public
    { Public declarations }
  end;

var
  FRMMCPClient: TFRMMCPClient;

implementation

uses
  sgcJSON;

{$R *.dfm}

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
  End;
end;

procedure TFRMMCPClient.Button2Click(Sender: TObject);
var
  oJSON: TsgcJSON;
begin
  oJSON := TsgcJSON.Create(nil);
  Try
    oJSON.AddPair('code', 'ShowMessage(''Hello World'')');
    MCP.RequestPrompt('CodeReview', oJSON);
  Finally
    oJSON.Free;
  End;
end;

procedure TFRMMCPClient.DoLog(const aText: string);
begin
  if Assigned(memoLog) then
    memoLog.Lines.Add(aText);
end;

procedure TFRMMCPClient.MCPMCPInitialize(Sender: TObject;
  const aRequest: TsgcAI_MCP_Request_Initialize;
  const aResponse: TsgcAI_MCP_Response_Initialize; var Accept: Boolean);
begin
  Accept := True;
  DoLog('#initialized');
end;

procedure TFRMMCPClient.MCPMCPListPrompts(Sender: TObject;
  const aRequest: TsgcAI_MCP_Request_PromptsList;
  const aResponse: TsgcAI_MCP_Response_PromptsList);
begin
  DoLog(aResponse.Raw);
end;

procedure TFRMMCPClient.MCPMCPListResources(Sender: TObject;
  const aRequest: TsgcAI_MCP_Request_ResourcesList;
  const aResponse: TsgcAI_MCP_Response_ResourcesList);
begin
  DoLog(aResponse.Raw);
end;

procedure TFRMMCPClient.MCPMCPListTools(Sender: TObject;
  const aRequest: TsgcAI_MCP_Request_ToolsList;
  const aResponse: TsgcAI_MCP_Response_ToolsList);
begin
  DoLog(aResponse.Raw);
end;

procedure TFRMMCPClient.MCPMCPResponsePrompt(Sender: TObject;
  const aRequest: TsgcAI_MCP_Request_PromptsGet;
  const aResponse: TsgcAI_MCP_Response_PromptsGet);
begin
  DoLog(aResponse.Raw);
end;

procedure TFRMMCPClient.MCPMCPResponseResource(Sender: TObject;
  const aRequest: TsgcAI_MCP_Request_ResourcesRead;
  const aResponse: TsgcAI_MCP_Response_ResourcesRead);
begin
  DoLog(aResponse.Raw);
end;

procedure TFRMMCPClient.MCPMCPResponseTool(Sender: TObject;
  const aRequest: TsgcAI_MCP_Request_ToolsCall;
  const aResponse: TsgcAI_MCP_Response_ToolsCall);
begin
  DoLog(aResponse.Raw);
end;

procedure TFRMMCPClient.MCPMCPStreamMessage(Sender: TObject;
  const aMessage: string; var Cancel: Boolean);
begin
  DoLog(aMessage);
end;

end.
```

