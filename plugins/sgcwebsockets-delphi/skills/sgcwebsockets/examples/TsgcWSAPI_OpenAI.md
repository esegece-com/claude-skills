# TsgcWSAPI_OpenAI - Example

Usage of `TsgcWSAPI_OpenAI` extracted from the **15.AI/01.QuickStart/06.RealTime** demo. See the full project for context.

API reference: [TsgcWSAPI_OpenAI](../reference/api/TsgcWSAPI_OpenAI.md)
Source demo: `15.AI/01.QuickStart/06.RealTime` (file `fOpenAI_RealTime.pas`)

```pascal
procedure TfrmOpenAI_RealTime.btnTranscriptionStartClick(Sender: TObject);
  begin
  WSOpenAI.OpenAIOptions.Method := sgcoaimTranscription;
  WSOpenAI.Client := WSClient;
  WSClient.Active := True;
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

WSOpenAI.OpenAIOptions.AzureOptions.ResourceName);
WSOpenAI.OpenAIOptions.AzureOptions.DeploymentId);
WSOpenAI.OpenAIOptions.AzureOptions.APIVersion);
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

```

