# TsgcAIOpenAIAssistant - Example

Full source of `fOpenAIAssistant.pas` from the **15.AI/02.Applications/05.Assistant** demo, which uses `TsgcAIOpenAIAssistant`.

API reference: [TsgcAIOpenAIAssistant](../reference/api/TsgcAIOpenAIAssistant.md)
Source demo: `15.AI/02.Applications/05.Assistant` (file `fOpenAIAssistant.pas`)

```pascal
ï»¿unit fOpenAIAssistant;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls, ExtCtrls, ComCtrls,
  ImgList, Menus, ImageList, UITypes,
  // sgc
  sgcAI, sgcAI_OpenAI, sgcAI_OpenAI_Audio, sgcHTTP_API_OpenAI,
  sgcAI_OpenAI_Audio_Assistant, sgcBase_Classes;

type
  TsgcAssistantIcons = (iconPlay, iconStop);

  TFRMOpenAIAssistant = class(TForm)
    pnlClient: TPanel;
    memoLog: TMemo;
    pageMain: TPageControl;
    tabLog: TTabSheet;
    tabConfiguration: TTabSheet;
    pageConfiguration: TPageControl;
    pnlConfigurationTop: TPanel;
    Label1: TLabel;
    txtAPIKey: TEdit;
    pnlConfigurationClient: TPanel;
    Assistant: TsgcAIOpenAIAssistant;
    tabAssistant: TTabSheet;
    txtAssistantName: TEdit;
    Label2: TLabel;
    memoAssistantInstructions: TMemo;
    Label3: TLabel;
    Label4: TLabel;
    txtAssistantModel: TEdit;
    chkAssistantFileSearch: TCheckBox;
    chkAssistantCodeInterpreter: TCheckBox;
    trackAssistantTemperature: TTrackBar;
    Label5: TLabel;
    Label6: TLabel;
    trackAssistantTopP: TTrackBar;
    pnlTop: TPanel;
    btnSendMessage: TButton;
    memoMessage: TMemo;
    Label7: TLabel;
    btnCreateAssistant: TButton;
    cboAssistant: TComboBox;
    Label8: TLabel;
    txtVectorStore: TEdit;
    Label9: TLabel;
    cboVectorStoreFiles: TComboBox;
    Label10: TLabel;
    btnVectorStoreUploadFile: TButton;
    btnLoadAssistants: TButton;
    chkStreaming: TCheckBox;
    chkAssistantFunctionCalling: TCheckBox;
    memoAssistantFunctionCalling: TMemo;
    procedure AssistantFunctionCall(Sender: TObject;
      const aRequest: TsgcOpenAIClass_ToolCall;
      const aResponse: TsgcHTTPOpenAI_ToolCall_Response);
    procedure AssistantStreamDone(Sender: TObject);
    procedure AssistantStreamError(Sender: TObject; const aError: string);
    procedure AssistantStreamMessage(Sender: TObject; const aEvent: string;
      const aMessage: TsgcOpenAIClass_Message; const aRaw: string);
    procedure AssistantStreamMessageDelta(Sender: TObject;
      const aMessageDelta: TsgcOpenAIClass_MessageDelta; const aRaw: string);
    procedure btnCreateAssistantClick(Sender: TObject);
    procedure btnLoadAssistantsClick(Sender: TObject);
    procedure btnSendMessageClick(Sender: TObject);
    procedure btnVectorStoreUploadFileClick(Sender: TObject);
    procedure cboAssistantChange(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure FormCreate(Sender: TObject);
  private
    FAssistant: TsgcOpenAIClass_Assistant;
    FThread: TsgcOpenAIClass_Thread;
    FAssistantId: string;
    FLoadAssistant: Boolean;
    FStreamMessage: TsgcOpenAIClass_Message;
    FStreamRun: TsgcOpenAIClass_Run;
    procedure DoLog(const aText: string);
  private
    procedure DoLoadSettings;
    procedure DoSaveSettings;
  private
    function DoFormatResponse(const aText: string): string;
    function DoCreateAssistant: Boolean;
    procedure DoLoadAssistants(const aAssistantId: string = '');
    procedure DoInitialize;
    procedure DoSendMessage;
    procedure DoSendMessageStreaming;
    procedure DoUpdateVectorStoreFiles;
  end;

var
  FRMOpenAIAssistant: TFRMOpenAIAssistant;

implementation

{$R *.dfm}

uses
  INIFiles, StrUtils, sgcBase_Helpers;

procedure TFRMOpenAIAssistant.AssistantFunctionCall(Sender: TObject;
  const aRequest: TsgcOpenAIClass_ToolCall;
  const aResponse: TsgcHTTPOpenAI_ToolCall_Response);
begin
  if aRequest._Function._Name = 'get_current_temperature' then
    aResponse.Output := '{"temperature": "' +
      InputBox('Get Current Temperature', 'Introduce the current temperature',
      '30') + '", "units": "Celsius"}'
  else if aRequest._Function._Name = 'get_rain_probability' then
    aResponse.Output := '{"probability": "' + InputBox('Get Rain Probability',
      'Introduce the Rain Probability', '10') + '"}';
end;

procedure TFRMOpenAIAssistant.AssistantStreamDone(Sender: TObject);
begin
  sgcFree(FStreamMessage);
  sgcFree(FStreamRun);
end;

procedure TFRMOpenAIAssistant.AssistantStreamError(Sender: TObject;
  const aError: string);
begin
  DoLog('#error: ' + aError);
end;

procedure TFRMOpenAIAssistant.AssistantStreamMessage(Sender: TObject;
  const aEvent: string; const aMessage: TsgcOpenAIClass_Message;
  const aRaw: string);
begin
  if aEvent = 'thread.message.created' then
    DoLog('[assistant]: ');
end;

procedure TFRMOpenAIAssistant.AssistantStreamMessageDelta(Sender: TObject;
  const aMessageDelta: TsgcOpenAIClass_MessageDelta; const aRaw: string);
var
  i: Integer;
  vText: string;
  vType: string;
begin
  for i := Low(aMessageDelta.Content) to High(aMessageDelta.Content) do
  begin
    vType := aMessageDelta.Content[i]._Type;
    if vType = 'text' then
    begin
      vText := TsgcOpenAIClass_MessageDeltaContent_Text
        (aMessageDelta.Content[i]).Value;
      memoLog.Lines.Text := memoLog.Lines.Text + vText;
      memoLog.Update;
    end;
  end;
end;

procedure TFRMOpenAIAssistant.btnCreateAssistantClick(Sender: TObject);
begin
  FAssistantId := '';
  if DoCreateAssistant then
    pageMain.ActivePage := tabLog;
end;

procedure TFRMOpenAIAssistant.btnLoadAssistantsClick(Sender: TObject);
begin
  DoLoadAssistants;
end;

procedure TFRMOpenAIAssistant.btnSendMessageClick(Sender: TObject);
begin
  if not Assigned(FAssistant) then
    raise Exception.Create('Before send a message create an Assistant!!!');
  if not Assigned(FThread) then
    raise Exception.Create('Before send a message create a Thread!!!');

  DoLog('[user]: ' + memoMessage.Lines.Text);
  if chkStreaming.Checked then
    DoSendMessageStreaming
  else
    DoSendMessage;
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
  Finally
    oDialog.Free;
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
  else
  // assistant using the demo sample
  begin
    case cboAssistant.ItemIndex of
      0:
        begin
          txtAssistantName.Text := 'Delphi Math Tutor';
          memoAssistantInstructions.Lines.Text :=
            'You are a personal math tutor. ' +
            'Answer questions briefly, in a sentence or less. When asked a question, use Delphi'
            + 'code to answer the question.';
          chkAssistantFileSearch.Checked := False;
          chkAssistantCodeInterpreter.Checked := True;
          chkAssistantFunctionCalling.Checked := False;
          memoMessage.Lines.Text :=
            'I need to solve the equation `3x + 11 = 14`. Can you help me?';
          memoAssistantFunctionCalling.Lines.Text := '';
        end;
      1:
        begin
          txtAssistantName.Text := 'sgcWebSockets HelpDesk';
          memoAssistantInstructions.Lines.Text :=
            'You are a sgcWebSockets HelpDesk Agent. ' +
            'Answer questions briefly, in a sentence or less. When asked a question, '
            + 'use the manual to answer the question.';
          chkAssistantFileSearch.Checked := True;
          chkAssistantCodeInterpreter.Checked := False;
          chkAssistantFunctionCalling.Checked := False;
          memoMessage.Lines.Text :=
            'Create a Delphi WebSocketClient that connects ' +
            'to eSeGeCe WebSocket server and when the message is received it echoes to the server.';
          memoAssistantFunctionCalling.Lines.Text := '';
        end;
      2:
        begin
          txtAssistantName.Text := 'Delphi Weather Bot';
          memoAssistantInstructions.Lines.Text :=
            'You are a weather bot. Use the provided functions to answer questions.';
          chkAssistantFileSearch.Checked := False;
          chkAssistantCodeInterpreter.Checked := False;
          chkAssistantFunctionCalling.Checked := True;
          memoMessage.Lines.Text :=
            'What is the weather in San Francisco today and the likelihood it will rain?';
          memoAssistantFunctionCalling.Lines.Text :=
            '[{"type":"function","function":{"name":"get_current_temperature","description":"Get the current temperature for a specific location","parameters":{"type":"object","properties":{"location":{"type":"string","description":"The city and state, e.g., San Francisco, CA"},'
            + '"unit":{"type":"string","enum":["Celsius","Fahrenheit"],"description":"The temperature unit to use. Infer this from the user location."}},"required":["location","unit"]}}},{"type":"function","function":{"name":"get_rain_probability","description":"Get the probability of rain for a specific location",'
            + '"parameters":{"type":"object","properties":{"location":{"type":"string","description":"The city and state, e.g., San Francisco, CA"}},"required":["location"]}}}]';
        end;
    end;
  end;
end;

function TFRMOpenAIAssistant.DoFormatResponse(const aText: string): string;
begin
  result := aText;
  result := sgcStringReplace(result, '\n', #13#10);
  result := sgcStringReplace(result, '\\', '');
end;

procedure TFRMOpenAIAssistant.FormDestroy(Sender: TObject);
begin
  DoSaveSettings;
end;

procedure TFRMOpenAIAssistant.FormCreate(Sender: TObject);
begin
  Try
    // settings
    DoLoadSettings;
    // visible
    if txtAPIKey.Text = '' then
    begin
      pageMain.ActivePage := tabConfiguration;
    end
    else
    begin
      pageMain.ActivePage := tabLog;
      if FLoadAssistant then
        DoLoadAssistants(FAssistantId)
      else
        DoCreateAssistant;
    end;
  Except
    On E: Exception do
    begin
      MessageDlg('Initialization error: ' + E.Message, mtError, [mbOk],
        0, mbOk);
      Application.Terminate;
    end;
  End;
end;

procedure TFRMOpenAIAssistant.DoLoadSettings;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    txtAPIKey.Text := oINI.ReadString('OPENAI', 'API_KEY', '');

    // assistant
    FAssistantId := oINI.ReadString('ASSISTANT', 'ID', '');
    FLoadAssistant := oINI.ReadBool('ASSISTANT', 'LOAD', False);
    if FLoadAssistant then
      DoLoadAssistants;
    cboAssistant.ItemIndex := oINI.ReadInteger('ASSISTANT', 'TYPE', 0);
    txtAssistantName.Text := oINI.ReadString('ASSISTANT', 'NAME',
      txtAssistantName.Text);
    cboAssistantChange(cboAssistant);
    memoAssistantInstructions.Lines.Text := oINI.ReadString('ASSISTANT',
      'INSTRUCTIONS', memoAssistantInstructions.Lines.Text);
    txtAssistantModel.Text := oINI.ReadString('ASSISTANT', 'MODEL',
      txtAssistantModel.Text);
    chkAssistantFileSearch.Checked := oINI.ReadBool('ASSISTANT', 'FILE_SEARCH',
      chkAssistantFileSearch.Checked);
    chkAssistantCodeInterpreter.Checked := oINI.ReadBool('ASSISTANT',
      'CODE_INTERPRETER', chkAssistantCodeInterpreter.Checked);
    chkAssistantFunctionCalling.Checked := oINI.ReadBool('ASSISTANT',
      'FUNCTION_CALLING', chkAssistantCodeInterpreter.Checked);
    trackAssistantTemperature.Position := oINI.ReadInteger('ASSISTANT',
      'TEMPERATURE', trackAssistantTemperature.Position);
    trackAssistantTopP.Position := oINI.ReadInteger('ASSISTANT', 'TOPP',
      trackAssistantTopP.Position);
  Finally
    oINI.Free;
  End;
end;

procedure TFRMOpenAIAssistant.DoLog(const aText: string);
begin
  memoLog.Lines.Add(aText);
end;

procedure TFRMOpenAIAssistant.DoSaveSettings;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    oINI.Writestring('OPENAI', 'API_KEY', txtAPIKey.Text);

    // assistant
    if Assigned(FAssistant) then
      oINI.Writestring('ASSISTANT', 'ID', FAssistantId)
    else
      oINI.Writestring('ASSISTANT', 'ID', '');
    oINI.WriteBool('ASSISTANT', 'LOAD', FLoadAssistant);
    oINI.WriteInteger('ASSISTANT', 'TYPE', cboAssistant.ItemIndex);
    oINI.Writestring('ASSISTANT', 'NAME', txtAssistantName.Text);
    oINI.Writestring('ASSISTANT', 'INSTRUCTIONS',
      memoAssistantInstructions.Lines.Text);
    oINI.Writestring('ASSISTANT', 'MODEL', txtAssistantModel.Text);
    oINI.WriteBool('ASSISTANT', 'FILE_SEARCH', chkAssistantFileSearch.Checked);
    oINI.WriteBool('ASSISTANT', 'CODE_INTERPRETER',
      chkAssistantCodeInterpreter.Checked);
    oINI.WriteBool('ASSISTANT', 'FUNCTION_CALLING',
      chkAssistantFunctionCalling.Checked);
    oINI.WriteInteger('ASSISTANT', 'TEMPERATURE',
      trackAssistantTemperature.Position);
    oINI.WriteInteger('ASSISTANT', 'TOPP', trackAssistantTopP.Position);
  Finally
    oINI.Free;
  End;
end;

function TFRMOpenAIAssistant.DoCreateAssistant: Boolean;
begin
  DoInitialize;

  Assistant.AssistantOptions.Name := txtAssistantName.Text;
  Assistant.AssistantOptions.Instructions.Text :=
    memoAssistantInstructions.Lines.Text;
  Assistant.AssistantOptions.Model := txtAssistantModel.Text;
  Assistant.AssistantOptions.Tools.FileSearch.Enabled :=
    chkAssistantFileSearch.Checked;
  Assistant.AssistantOptions.Tools.CodeInterpreter.Enabled :=
    chkAssistantCodeInterpreter.Checked;
  Assistant.AssistantOptions.Tools.Functions.Enabled :=
    chkAssistantFunctionCalling.Checked;
  Assistant.AssistantOptions.Tools.Functions.Functions.Text :=
    memoAssistantFunctionCalling.Lines.Text;

  Assistant.AssistantOptions.Temperature := trackAssistantTemperature.Position;
  Assistant.AssistantOptions.TopP := trackAssistantTopP.Position;

  if FAssistantId = '' then
  begin
    FAssistant := Assistant.CreateAssistant;
    if Assigned(FAssistant) then
    begin
      FThread := Assistant.CreateThread;
      DoLog('#create assistant: ' + FAssistant.Id);
    end;
  end
  else
  begin
    FAssistant := Assistant.GetAssistant(FAssistantId);
    if Assigned(FAssistant) then
      FThread := Assistant.CreateThread;
  end;
  DoUpdateVectorStoreFiles;

  if Assigned(FAssistant) then
    FAssistantId := FAssistant.Id;

  result := (FAssistantId <> '') and Assigned(FThread);
  if result and (cboAssistant.ItemIndex = 1) then
    result := cboVectorStoreFiles.Items.Count > 0;
end;

procedure TFRMOpenAIAssistant.DoInitialize;
begin
  if txtAPIKey.Text = '' then
    raise Exception.Create('Set First the OpenAI API Key!!!');

  Assistant.OpenAIOptions.ApiKey := txtAPIKey.Text;
end;

procedure TFRMOpenAIAssistant.DoLoadAssistants(const aAssistantId: string = '');
var
  i: Integer;
  oAssistant: TsgcOpenAIClass_Assistant;
  oResponse: TsgcOpenAIClass_Response_List_Assistants;
begin
  DoInitialize;

  cboAssistant.Items.Clear;

  oResponse := Assistant.ListAssistants;
  Try
    if Assigned(oResponse) then
    begin
      for i := Low(oResponse.Asisstants) to High(oResponse.Asisstants) do
      begin
        oAssistant := oResponse.Asisstants[i];
        cboAssistant.Items.Add(oAssistant.Id);
        if oAssistant.Id = aAssistantId then
          cboAssistant.ItemIndex := i;
      end;
    end;
  Finally
    FreeAndNil(oResponse);
  End;
end;

procedure TFRMOpenAIAssistant.DoSendMessage;
var
  i: Integer;
  oMessage: TsgcOpenAIClass_Message;
  oMessages: TsgcOpenAIClass_Response_List_Messages;
  oRun: TsgcOpenAIClass_Run;
begin
  Screen.Cursor := crHourGlass;
  Try
    oMessage := Assistant.CreateMessageText(FThread.Id, memoMessage.Lines.Text);
    if Assigned(oMessage) then
    begin
      oRun := Assistant.CreateRunAndWait(FThread.Id);
      if Assigned(oRun) then
      begin
        oMessages := Assistant.GetMessages(FThread.Id, oRun.Id);
        if Assigned(oMessages) and (Length(oMessages.Messages) > 0) then
        begin
          memoMessage.Lines.Text := '';
          for i := 0 to Length(oMessages.Messages) - 1 do
            DoLog('[assistant]: ' + DoFormatResponse(oMessages.Messages[i]
              .ContentText + #13#10));
        end;
      end;
    end;
  Finally
    Screen.Cursor := crDefault;
  End;
end;

procedure TFRMOpenAIAssistant.DoSendMessageStreaming;
begin
  FStreamMessage := Assistant.CreateMessageText(FThread.Id,
    memoMessage.Lines.Text);
  if Assigned(FStreamMessage) then
    FStreamRun := Assistant.CreateRun(FThread.Id, True);
end;

procedure TFRMOpenAIAssistant.DoUpdateVectorStoreFiles;
var
  i: Integer;
  oVectorStoreFile: TsgcOpenAIClass_VectorStoreFile;
  oVectorStoreFiles: TsgcOpenAIClass_Response_List_VectorStoreFiles;
begin
  cboVectorStoreFiles.Items.Clear;
  oVectorStoreFiles := Assistant.GetVectorStoreFiles(txtVectorStore.Text);
  if Assigned(oVectorStoreFiles) then
  begin
    for i := Low(oVectorStoreFiles.VectorStoreFiles)
      to High(oVectorStoreFiles.VectorStoreFiles) do
    begin
      oVectorStoreFile := oVectorStoreFiles.VectorStoreFiles[i];
      cboVectorStoreFiles.Items.Add(oVectorStoreFile.Id);
    end;
  end;
end;

end.
```

