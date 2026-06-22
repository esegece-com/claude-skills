# TsgcAIOpenAIEmbeddings - Example

Full source of `fQuestionsAnswers.pas` from the **15.AI/02.Applications/03.QA** demo, which uses `TsgcAIOpenAIEmbeddings`.

API reference: [TsgcAIOpenAIEmbeddings](../reference/api/TsgcAIOpenAIEmbeddings.md)
Source demo: `15.AI/02.Applications/03.QA` (file `fQuestionsAnswers.pas`)

```pascal
unit fQuestionsAnswers;

interface

uses
  Winapi.Windows, Winapi.Messages, System.SysUtils, System.Variants, System.Classes, Vcl.Graphics,
  Vcl.Controls, Vcl.Forms, Vcl.Dialogs, sgcBase_Classes, sgcAI_OpenAI,
  sgcAI_OpenAI_Audio, sgcAI_OpenAI_Audio_ChatBot, sgcAI, Vcl.StdCtrls,
  Vcl.ExtCtrls, sgcAI_OpenAI_Embeddings, sgcAI_DB_Vector, sgcAI_DB_Vector_File,
  Vcl.ComCtrls, sgcAI_DB_Vector_Pinecone;

type
  TFRMQuestionsAnswers = class(TForm)
    pnlClient: TPanel;
    memoLog: TMemo;
    pnlTop: TPanel;
    Label1: TLabel;
    txtAPIKey: TEdit;
    txtQuestion: TEdit;
    Label2: TLabel;
    btnAskChatGPT: TButton;
    ChatBot: TsgcAIOpenAIChatBot;
    Embeddings: TsgcAIOpenAIEmbeddings;
    PageControlDB: TPageControl;
    tabFile: TTabSheet;
    Label3: TLabel;
    Label4: TLabel;
    txtFileInputFilename: TEdit;
    txtFileVectorFilename: TEdit;
    tabPinecone: TTabSheet;
    lblApiKey: TLabel;
    Label21: TLabel;
    Label8: TLabel;
    Label9: TLabel;
    txtPineconeApiKey: TEdit;
    txtPineconeEnvironment: TEdit;
    txtPineconeIndexName: TEdit;
    txtPineconeProjectId: TEdit;
    Label5: TLabel;
    cboDatabase: TComboBox;
    DBVectorFile: TsgcAIDatabaseVectorFile;
    DBVectorPinecone: TsgcAIDatabaseVectorPinecone;
    cboPredefinedAnswers: TComboBox;
    Label6: TLabel;
    lblWarning: TLabel;
    procedure btnAskChatGPTClick(Sender: TObject);
    procedure cboDatabaseChange(Sender: TObject);
    procedure cboPredefinedAnswersChange(Sender: TObject);
    procedure ChatBotChatCompletion(Sender: TObject; const Role, Content: string);
    procedure FormCreate(Sender: TObject);
    procedure FormDestroy(Sender: TObject);
    procedure txtAPIKeyChange(Sender: TObject);
    procedure txtFileInputFilenameChange(Sender: TObject);
    procedure txtFileVectorFilenameChange(Sender: TObject);
    procedure txtPineconeApiKeyChange(Sender: TObject);
    procedure txtPineconeEnvironmentChange(Sender: TObject);
    procedure txtPineconeIndexNameChange(Sender: TObject);
    procedure txtPineconeProjectIdChange(Sender: TObject);
  private
    procedure DoLog(const aText: string);
  private
    procedure DoLoadSettings;
    procedure DoSaveSettings;
  private
    function GetContextFromPinecone(const aContext: string): string;
  end;

var
  FRMQuestionsAnswers: TFRMQuestionsAnswers;

implementation

uses
  INIFiles,
  sgcBase_Helpers, sgcJSON;

{$R *.dfm}

procedure TFRMQuestionsAnswers.btnAskChatGPTClick(Sender: TObject);
var
  vContext: string;
begin
  case cboDatabase.ItemIndex of
    1: Embeddings.Database := DBVectorPinecone;
    else
      Embeddings.Database := DBVectorFile;
  end;

  memoLog.Lines.Clear;
  DoLog('[me] ' + txtQuestion.Text);
  vContext := ChatBot.GetEmbedding(txtQuestion.Text);

  if cboDatabase.ItemIndex = 1 then
    vContext := GetContextFromPinecone(vContext);

  ChatBot.ChatAsUser('Answer the question based on the context below.\n\nContext:\n' + vContext + '\nQuestion:' + txtQuestion.Text + '\nAnswer:');

  txtQuestion.Text := '';
end;

procedure TFRMQuestionsAnswers.cboDatabaseChange(Sender: TObject);
begin
  pageControlDB.ActivePageIndex := cboDatabase.ItemIndex;
  lblWarning.Visible := cboDatabase.ItemIndex = 0;
end;

procedure TFRMQuestionsAnswers.cboPredefinedAnswersChange(Sender: TObject);
begin
  txtQuestion.Text := cboPredefinedAnswers.Items[cboPredefinedAnswers.ItemIndex];
end;

procedure TFRMQuestionsAnswers.ChatBotChatCompletion(Sender: TObject; const
    Role, Content: string);
begin
  DoLog('[' + Role + '] ' + Content);
end;

procedure TFRMQuestionsAnswers.DoLoadSettings;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    txtApiKey.Text := oINI.ReadString('OPENAI', 'API_KEY', '');

    cboDatabase.ItemIndex := oINI.ReadInteger('DB', 'TYPE', 0);

    txtFileInputFilename.Text := oINI.ReadString('DB.FILE', 'INPUT_FILENAME', 'sgcEmbeddings.sgcif');
    txtFileVectorFilename.Text := oINI.ReadString('DB.FILE', 'VECTOR_FILENAME', 'sgcEmbeddings.sgcvf');

    txtPineconeApiKey.Text := oINI.ReadString('DB.PINECONE', 'API_KEY', '');
    txtPineconeEnvironment.Text := oINI.ReadString('DB.PINECONE', 'ENVIRONMENT', 'us-west4-gcp-free');
    txtPineconeIndexName.Text := oINI.ReadString('DB.PINECONE.INDEX', 'INDEX_NAME', '');
    txtPineconeProjectId.Text := oINI.ReadString('DB.PINECONE.INDEX', 'PROJECT_ID', '');
  Finally
    oINI.Free;
  End;
end;

procedure TFRMQuestionsAnswers.FormCreate(Sender: TObject);
var
  i: integer;
begin
  DoLoadSettings;

  for i := 0 to PageControlDB.PageCount - 1 do
    PageControlDB.Pages[i].TabVisible := false;
  PageControlDB.ActivePageIndex := cboDatabase.ItemIndex;
end;

procedure TFRMQuestionsAnswers.FormDestroy(Sender: TObject);
begin
  DoSaveSettings;
end;

procedure TFRMQuestionsAnswers.DoLog(const aText: string);
begin
  memoLog.Lines.Add(sgcStringReplace(aText, #10, #13#10));
end;

procedure TFRMQuestionsAnswers.DoSaveSettings;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    oINI.Writestring('OPENAI', 'API_KEY', txtApiKey.Text);

    oINI.WriteInteger('DB', 'TYPE', cboDatabase.ItemIndex);

    oINI.Writestring('DB.FILE', 'INPUT_FILENAME', txtFileInputFilename.Text);
    oINI.Writestring('DB.FILE', 'VECTOR_FILENAME', txtFileVectorFilename.Text);

    oINI.Writestring('DB.PINECONE', 'API_KEY', txtPineconeApiKey.Text);
    oINI.Writestring('DB.PINECONE', 'ENVIRONMENT', txtPineconeEnvironment.Text);
    oINI.WriteString('DB.PINECONE.INDEX', 'INDEX_NAME', txtPineconeIndexName.Text);
    oINI.WriteString('DB.PINECONE.INDEX', 'PROJECT_ID', txtPineconeProjectId.Text);
  Finally
    oINI.Free;
  End;
end;

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
  Finally
    oJSON.Free;
  End;
end;

procedure TFRMQuestionsAnswers.txtAPIKeyChange(Sender: TObject);
begin
  ChatBot.OpenAIOptions.ApiKey := txtAPIKey.Text;
  Embeddings.OpenAIOptions.ApiKey := txtAPIKey.Text;
end;

procedure TFRMQuestionsAnswers.txtFileInputFilenameChange(Sender: TObject);
begin
  DBVectorFile.VectorFileOptions.InputFilename := txtFileInputFilename.Text;
end;

procedure TFRMQuestionsAnswers.txtFileVectorFilenameChange(Sender: TObject);
begin
  DBVectorFile.VectorFileOptions.VectorFilename := txtFileVectorFilename.Text;
end;

procedure TFRMQuestionsAnswers.txtPineconeApiKeyChange(Sender: TObject);
begin
  DBVectorPinecone.PineconeOptions.ApiKey := txtPineconeApiKey.Text;
end;

procedure TFRMQuestionsAnswers.txtPineconeEnvironmentChange(Sender: TObject);
begin
  DBVectorPinecone.PineconeOptions.Environment := txtPineconeEnvironment.Text;
end;

procedure TFRMQuestionsAnswers.txtPineconeIndexNameChange(Sender: TObject);
begin
  DBVectorPinecone.PineconeIndexOptions.IndexName := txtPineconeIndexName.Text;
end;

procedure TFRMQuestionsAnswers.txtPineconeProjectIdChange(Sender: TObject);
begin
  DBVectorPinecone.PineconeIndexOptions.ProjectId := txtPineconeProjectId.Text;
end;

end.
```

