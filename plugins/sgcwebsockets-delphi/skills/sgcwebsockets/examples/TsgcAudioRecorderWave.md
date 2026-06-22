# TsgcAudioRecorderWave - Example

Full source of `fOpenAI_RealTime.pas` from the **15.AI/01.QuickStart/06.RealTime** demo, which uses `TsgcAudioRecorderWave`.

API reference: [TsgcAudioRecorderWave](../reference/api/TsgcAudioRecorderWave.md)
Source demo: `15.AI/01.QuickStart/06.RealTime` (file `fOpenAI_RealTime.pas`)

```pascal
unit fOpenAI_RealTime;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, ExtCtrls, ComCtrls, StdCtrls,
  // sgc
  sgcBase_Classes, sgcSocket_Classes,
  sgcTCP_Classes, sgcWebSocket_Classes, sgcWebSocket_API_OpenAI,
  sgcWebSocket_APIs, sgcWebSocket_Classes_Indy, sgcWebSocket_Client,
  sgcWebSocket, sgcAI_AudioRecorder, sgcAI_AudioRecorder_Wave, sgcAI;

type
  TfrmOpenAI_RealTime = class(TForm)
    pnlTop: TPanel;
    txtApiKey: TEdit;
    lblApiKey: TLabel;
    lblOrganization: TLabel;
    txtOrganization: TEdit;
    memoLog: TMemo;
    pageProvider: TPageControl;
    tabOpenAI: TTabSheet;
    pnlProvider: TPanel;
    tabAzure: TTabSheet;
    cboProvider: TComboBox;
    Label1: TLabel;
    Label2: TLabel;
    txtAzureResourceName: TEdit;
    Label3: TLabel;
    txtAzureDeploymentId: TEdit;
    txtAzureAPIVersion: TEdit;
    Label4: TLabel;
    PageControl1: TPageControl;
    tabTranscription: TTabSheet;
    WSOpenAI: TsgcWSAPI_OpenAI;
    WSClient: TsgcWebSocketClient;
    btnTranscriptionStart: TButton;
    btnTranscriptionStop: TButton;
    sgcAudioRecorder: TsgcAudioRecorderWave;
    procedure btnTranscriptionStartClick(Sender: TObject);
    procedure btnTranscriptionStopClick(Sender: TObject);
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure txtApiKeyChange(Sender: TObject);
    procedure cboProviderChange(Sender: TObject);
    procedure txtAzureAPIVersionChange(Sender: TObject);
    procedure txtAzureDeploymentIdChange(Sender: TObject);
    procedure txtAzureResourceNameChange(Sender: TObject);
    procedure WSOpenAIConnect(Connection: TsgcWSConnection);
    procedure WSOpenAIDisconnect(Connection: TsgcWSConnection; Code: Integer);
    procedure WSOpenAIException(Connection: TsgcWSConnection; E: Exception);
    procedure WSOpenAIOpenAIAudioTranscriptionCompleted(Sender: TObject; const
        aItem: TsgcWSOpenAIConversation_Item_Completed);
    procedure WSOpenAIOpenAIAudioTranscriptionDelta(Sender: TObject; const aItem:
        TsgcWSOpenAIConversation_Item_Delta);
    procedure WSOpenAIOpenAIError(Sender: TObject; const aError: string);
  private
    procedure DoLoadSettings;
    procedure DoSaveSettings;
  public
    procedure DoLog(const aText: string);
  end;

var
  frmOpenAI_RealTime: TfrmOpenAI_RealTime;

implementation

{$R *.dfm}

uses
  INIFiles;

procedure TfrmOpenAI_RealTime.btnTranscriptionStartClick(Sender: TObject);
begin
  WSOpenAI.OpenAIOptions.Method := sgcoaimTranscription;
  WSOpenAI.Client := WSClient;
  WSClient.Active := True;
end;

procedure TfrmOpenAI_RealTime.btnTranscriptionStopClick(Sender: TObject);
begin
  WSClient.Active := False;
end;

procedure TfrmOpenAI_RealTime.FormCreate(Sender: TObject);

var
  i: integer;
begin
  for i := 1 to pageProvider.PageCount - 1 do
    pageProvider.Pages[i].TabVisible := false;

  DoLoadSettings;
end;

procedure TfrmOpenAI_RealTime.FormDestroy(Sender: TObject);
begin
  DoSaveSettings;
end;

procedure TfrmOpenAI_RealTime.cboProviderChange(Sender: TObject);
var
  i: integer;
begin
  for i := 0 to pageProvider.PageCount - 1 do
    pageProvider.Pages[i].TabVisible := false;

  case cboProvider.ItemIndex of
    1:
      begin
        pageProvider.ActivePage := tabAzure;
        WSOpenAI.OpenAIOptions.Provider := sgcoaipAzure;
        tabAzure.TabVisible := True;
      end
  else
    begin
      pageProvider.ActivePage := tabOpenAI;
      WSOpenAI.OpenAIOptions.Provider := sgcoaipOpenAI;
      tabOpenAI.TabVisible := True;
    end;
  end;
end;

procedure TfrmOpenAI_RealTime.DoLoadSettings;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    txtApiKey.Text := oINI.ReadString('OpenAI_RealTime', 'API_KEY', '');
    txtOrganization.Text := oINI.ReadString('OpenAI_RealTime',
      'ORGANIZATION', '');
    cboProvider.ItemIndex := oINI.ReadInteger('OpenAI_RealTime', 'PROVIDER', 0);
    cboProviderChange(cboProvider);

    txtAzureResourceName.Text := oINI.ReadString('AZURE', 'RESOURCE_NAME',
      WSOpenAI.OpenAIOptions.AzureOptions.ResourceName);
    txtAzureDeploymentId.Text := oINI.ReadString('AZURE', 'DEPLOYMENT_ID',
      WSOpenAI.OpenAIOptions.AzureOptions.DeploymentId);
    txtAzureAPIVersion.Text := oINI.ReadString('AZURE', 'API_VERSION',
      WSOpenAI.OpenAIOptions.AzureOptions.APIVersion);
  Finally
    oINI.Free;
  End;
end;

procedure TfrmOpenAI_RealTime.DoLog(const aText: string);
begin
  memoLog.Lines.Add(aText);
end;

procedure TfrmOpenAI_RealTime.DoSaveSettings;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    oINI.Writestring('OpenAI_RealTime', 'API_KEY', txtApiKey.Text);
    oINI.Writestring('OpenAI_RealTime', 'ORGANIZATION', txtOrganization.Text);
    oINI.WriteInteger('OpenAI_RealTime', 'PROVIDER', cboProvider.ItemIndex);

    oINI.Writestring('AZURE', 'RESOURCE_NAME', txtAzureResourceName.Text);
    oINI.Writestring('AZURE', 'DEPLOYMENT_ID', txtAzureDeploymentId.Text);
    oINI.Writestring('AZURE', 'API_VERSION', txtAzureAPIVersion.Text);
  Finally
    oINI.Free;
  End;
end;

procedure TfrmOpenAI_RealTime.txtApiKeyChange(Sender: TObject);
begin
  WSOpenAI.OpenAIOptions.ApiKey := txtApiKey.Text;
end;

procedure TfrmOpenAI_RealTime.txtAzureAPIVersionChange(Sender: TObject);
begin
  WSOpenAI.OpenAIOptions.AzureOptions.APIVersion := txtAzureAPIVersion.Text;
end;

procedure TfrmOpenAI_RealTime.txtAzureDeploymentIdChange(Sender: TObject);
begin
  WSOpenAI.OpenAIOptions.AzureOptions.DeploymentId := txtAzureDeploymentId.Text;
end;

procedure TfrmOpenAI_RealTime.txtAzureResourceNameChange(Sender: TObject);
begin
  WSOpenAI.OpenAIOptions.AzureOptions.ResourceName := txtAzureResourceName.Text;
end;

procedure TfrmOpenAI_RealTime.WSOpenAIConnect(Connection: TsgcWSConnection);
begin
  DoLog('#connected');
end;

procedure TfrmOpenAI_RealTime.WSOpenAIDisconnect(Connection: TsgcWSConnection;
    Code: Integer);
begin
  DoLog('#disconnected');
end;

procedure TfrmOpenAI_RealTime.WSOpenAIException(Connection: TsgcWSConnection;
    E: Exception);
begin
  DoLog('#exception: ' + E.Message);
end;

procedure TfrmOpenAI_RealTime.WSOpenAIOpenAIAudioTranscriptionCompleted(Sender:
    TObject; const aItem: TsgcWSOpenAIConversation_Item_Completed);
begin
  DoLog('#transcription_completed: ' + aItem.Transcript);
end;

procedure TfrmOpenAI_RealTime.WSOpenAIOpenAIAudioTranscriptionDelta(Sender:
    TObject; const aItem: TsgcWSOpenAIConversation_Item_Delta);
begin
  DoLog('#transcription_delta: ' + aItem.Delta);
end;

procedure TfrmOpenAI_RealTime.WSOpenAIOpenAIError(Sender: TObject; const
    aError: string);
begin
  DoLog('#openai_error: ' + aError);
end;

end.
```

