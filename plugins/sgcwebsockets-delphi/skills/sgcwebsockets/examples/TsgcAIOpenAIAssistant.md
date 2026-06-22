# TsgcAIOpenAIAssistant - Example

Usage of `TsgcAIOpenAIAssistant` extracted from the **15.AI/02.Applications/05.Assistant** demo. See the full project for context.

API reference: [TsgcAIOpenAIAssistant](../reference/api/TsgcAIOpenAIAssistant.md)
Source demo: `15.AI/02.Applications/05.Assistant` (file `fOpenAIAssistant.pas`)

```pascal
procedure TFRMOpenAIAssistant.btnCreateAssistantClick(Sender: TObject);
  begin
  FAssistantId := '';
  if DoCreateAssistant then
  pageMain.ActivePage := tabLog;
  end;

procedure TFRMOpenAIAssistant.btnVectorStoreUploadFileClick(Sender: TObject);
  var
  oDialog: TOpenDialog;
  begin
  if FAssistantId = '' then
  raise Exception.Create('Create First an Assistant!!!');
  
  oDialog := TOpenDialog.Create(nil);
  Try
  if oDialog.Execute then
  begin
  Screen.Cursor := crHourGlass;
  Try
  Assistant.UploadVectorStoreFile(txtVectorStore.Text, oDialog.FileName);
  DoUpdateVectorStoreFiles();
  FThread := Assistant.CreateThread;
  Finally
  Screen.Cursor := crDefault;
  End;
  end;

procedure TFRMOpenAIAssistant.cboAssistantChange(Sender: TObject);
  var
  i: Integer;
  begin
  FLoadAssistant := False;
  // loaded from existing assistants
  if LeftStr(cboAssistant.Text, 5) = 'asst_' then
  begin
  chkAssistantCodeInterpreter.Checked := False;
  chkAssistantFileSearch.Checked := False;
  
  FAssistant := Assistant.GetAssistant(cboAssistant.Text);
  if Assigned(FAssistant) then
  begin
  FThread := Assistant.CreateThread;
  
  FAssistantId := FAssistant.Id;
  txtAssistantName.Text := FAssistant.Name;
  memoAssistantInstructions.Lines.Text := FAssistant.Instructions;
  for i := Low(FAssistant.Tools) to High(FAssistant.Tools) do
  begin
  if FAssistant.Tools[i]._Type = 'code_interpreter' then
  chkAssistantCodeInterpreter.Checked := True;
  if FAssistant.Tools[i]._Type = 'file_search' then
  chkAssistantFileSearch.Checked := True;
  if FAssistant.Tools[i]._Type = 'function' then
  chkAssistantFunctionCalling.Checked := True;
  end;
  memoMessage.Lines.Text := '';
  FLoadAssistant := True;
  end;
  end
```

