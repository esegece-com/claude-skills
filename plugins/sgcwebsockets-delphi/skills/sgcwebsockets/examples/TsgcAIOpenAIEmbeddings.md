# TsgcAIOpenAIEmbeddings - Example

Usage of `TsgcAIOpenAIEmbeddings` extracted from the **15.AI/02.Applications/03.QA** demo. See the full project for context.

API reference: [TsgcAIOpenAIEmbeddings](../reference/api/TsgcAIOpenAIEmbeddings.md)
Source demo: `15.AI/02.Applications/03.QA` (file `fQuestionsAnswers.pas`)

```pascal
procedure TFRMQuestionsAnswers.btnAskChatGPTClick(Sender: TObject);
  var
  vContext: string;
  begin
  case cboDatabase.ItemIndex of
  1: Embeddings.Database := DBVectorPinecone;
  else
  Embeddings.Database := DBVectorFile;
  end;

txtFileInputFilename.Text := oINI.ReadString('DB.FILE', 'INPUT_FILENAME', 'sgcEmbeddings.sgcif');
txtFileVectorFilename.Text := oINI.ReadString('DB.FILE', 'VECTOR_FILENAME', 'sgcEmbeddings.sgcvf');
function TFRMQuestionsAnswers.GetContextFromPinecone(const aContext: string):
  string;
  var
  oFile: TStringList;
  oJSON: TsgcJSON;
  vId: Integer;
  begin
  result := '';
  
  oJSON := TsgcJSON.Create(nil);
  Try
  oJSON.Read(aContext);
  if oJSON.Node['matches'] <> nil then
  begin
  if oJSON.Node['matches'].JSONObject.Count > 0 then
  begin
  if oJSON.Node['matches'].JSONObject.Item[0].Node['id'] <> nil then
  begin
  // ... assuming the id is an integer for testing purposes
  TryStrToInt(oJSON.Node['matches'].JSONObject.Item[0].Node['id'].Value, vId);
  
  // ... load the input file text and get the prompt from the row number
  oFile := TStringList.Create;
  Try
  oFile.LoadFromFile('sgcEmbeddings.sgcif');
  result := oFile[vId];
  Finally
  oFile.Free;
  End;
  end;
  end;
  end;

procedure TFRMQuestionsAnswers.txtAPIKeyChange(Sender: TObject);
  begin
  ChatBot.OpenAIOptions.ApiKey := txtAPIKey.Text;
  Embeddings.OpenAIOptions.ApiKey := txtAPIKey.Text;
  end;

```

