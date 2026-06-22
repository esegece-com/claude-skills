# TsgcAIOpenAIChatBot - Example

Full source of `fOpenAIChatBot.pas` from the **15.AI/02.Applications/01.ChatBot** demo, which uses `TsgcAIOpenAIChatBot`.

API reference: [TsgcAIOpenAIChatBot](../reference/api/TsgcAIOpenAIChatBot.md)
Source demo: `15.AI/02.Applications/01.ChatBot` (file `fOpenAIChatBot.pas`)

```pascal
ï»¿unit fOpenAIChatBot;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls, ExtCtrls, ComCtrls,
  ImgList, Menus, ImageList, UITypes,
  // sgc
  sgcAI, fOpenAIChatBot_Controls, sgcBase_Classes, sgcAI_OpenAI,
  sgcAI_OpenAI_Audio, sgcAI_OpenAI_Audio_ChatBot, sgcAI_AudioRecorder,
  sgcAI_AudioRecorder_MCI, sgcAI_TextToSpeech, sgcAI_TextToSpeech_System,
  sgcAI_TextToSpeech_Google, sgcAI_AudioPlayer, sgcAI_AudioPlayer_MCI,
  sgcAI_TextToSpeech_Amazon;

type
  TsgcChatBotIcons = (iconPlay, iconStop);

  TFRMOpenAIChatBot = class(TForm)
    pnlClient: TPanel;
    memoLog: TMemo;
    pageMain: TPageControl;
    tabLog: TTabSheet;
    tabConfiguration: TTabSheet;
    pageConfiguration: TPageControl;
    tabSpeechToText: TTabSheet;
    pnlConfigurationTop: TPanel;
    Label1: TLabel;
    txtAPIKey: TEdit;
    pnlConfigurationClient: TPanel;
    cboSpeechToTextLanguage: TComboBox;
    lblLanguage: TLabel;
    tabTextToSpeech: TTabSheet;
    lblModel: TLabel;
    txtSpeechToTextModel: TEdit;
    txtSpeechToTextFilename: TEdit;
    Label2: TLabel;
    pageTextToSpeech: TPageControl;
    pnlTextToSpeechTop: TPanel;
    lblTextToSpeechProvider: TLabel;
    cboTextToSpeechProviders: TComboBox;
    pnlTextToSpeechClient: TPanel;
    tabTextToSpeechSystem: TTabSheet;
    tabTextToSpeechGoogle: TTabSheet;
    tabTextToSpeechAmazon: TTabSheet;
    Label3: TLabel;
    txtTextToSpeechAmazonAccessKey: TEdit;
    Label4: TLabel;
    txtTextToSpeechAmazonSecretKey: TEdit;
    Label5: TLabel;
    txtTextToSpeechAmazonRegion: TEdit;
    Label6: TLabel;
    cboTextToSpeechAmazonVoices: TComboBox;
    lblTextToSpeechGoogleSettings: TLabel;
    txtTextToSpeechGoogleSettings: TEdit;
    Label7: TLabel;
    cboTextToSpeechGoogleVoices: TComboBox;
    cboSpeechToTextCaptureAudio: TComboBox;
    lblSendAudio: TLabel;
    sgcTrayIcon: TTrayIcon;
    icons: TImageList;
    PopupMenu1: TPopupMenu;
    Configuration1: TMenuItem;
    Start1: TMenuItem;
    Stop1: TMenuItem;
    Exit1: TMenuItem;
    N1: TMenuItem;
    N2: TMenuItem;
    cboQuickConfiguration: TComboBox;
    Label8: TLabel;
    ChatBot: TsgcAIOpenAIChatBot;
    AudioRecorderMCI: TsgcAudioRecorderMCI;
    TextToSpeechSystem: TsgcTextToSpeechSystem;
    TextToSpeechGoogle: TsgcTextToSpeechGoogle;
    TextToSpeechAmazon: TsgcTextToSpeechAmazon;
    AudioPlayerMCI: TsgcAudioPlayerMCI;
    procedure cboQuickConfigurationChange(Sender: TObject);
    procedure cboTextToSpeechProvidersChange(Sender: TObject);
    procedure ChatBotAudioStart(Sender: TObject);
    procedure ChatBotAudioStop(Sender: TObject);
    procedure ChatBotChatCompletion(Sender: TObject; const Role, Content: string);
    procedure ChatBotTranscription(Sender: TObject; var Text: string; var Accept:
        Boolean);
    procedure Configuration1Click(Sender: TObject);
    procedure Exit1Click(Sender: TObject);
    procedure FormCloseQuery(Sender: TObject; var CanClose: Boolean);
    procedure FormDestroy(Sender: TObject);
    procedure FormCreate(Sender: TObject);
    procedure Start1Click(Sender: TObject);
    procedure Stop1Click(Sender: TObject);
  private
    procedure DoLog(const aText: string);
  private
    function GetTranscriptionLanguage: string;
    function GetAmazonVoiceId: string;
    function GetAmazonEngine: string;
    function GetGoogleVoiceId: string;
    function GetGoogleLanguage: string;
    function GetGoogleGender: string;
  private
    procedure DoLoadSettings;
    procedure DoSaveSettings;
  private
  private
  protected
    procedure DoQuickConfiguration(aItemIndex: Integer = -1); virtual;
  protected
    FListening: Boolean;
    procedure DoStart; virtual;
    procedure DoStop; virtual;
    procedure DoConfiguration; virtual;
    procedure DoApplicationExit; virtual;
  protected
    FFormControls: TFRMOpenAIChatBot_Controls;
    procedure OnControlStartEvent(Sender: TObject); virtual;
    procedure OnControlStopEvent(Sender: TObject); virtual;
    procedure OnControlConfigurationEvent(Sender: TObject); virtual;
    procedure OnControlExitEvent(Sender: TObject); virtual;
    procedure DoUpdateControlState(aListening: Boolean); virtual;
    procedure DoShowControls; virtual;
  end;

var
  FRMOpenAIChatBot: TFRMOpenAIChatBot;

implementation

{$R *.dfm}

uses
  INIFiles, StrUtils;

procedure TFRMOpenAIChatBot.cboQuickConfigurationChange(Sender: TObject);
begin
  if FListening then
    DoStop;

  DoQuickConfiguration;
end;

procedure TFRMOpenAIChatBot.cboTextToSpeechProvidersChange(Sender: TObject);
begin
  case cboTextToSpeechProviders.ItemIndex of
    0:
      pageTextToSpeech.ActivePage := tabTextToSpeechSystem;
    1:
      pageTextToSpeech.ActivePage := tabTextToSpeechGoogle;
    2:
      pageTextToSpeech.ActivePage := tabTextToSpeechAmazon;
  end;
end;

procedure TFRMOpenAIChatBot.ChatBotAudioStart(Sender: TObject);
begin
  FListening := True;
  DoUpdateControlState(True);
  DoLog('#audio start');
  sgcTrayIcon.IconIndex := Ord(iconPlay);
end;

procedure TFRMOpenAIChatBot.ChatBotAudioStop(Sender: TObject);
begin
  FListening := False;
  DoUpdateControlState(False);
  sgcTrayIcon.IconIndex := Ord(iconStop);
  DoLog('#audio stop');
end;

procedure TFRMOpenAIChatBot.ChatBotChatCompletion(Sender: TObject; const Role,
    Content: string);
begin
  DoLog('[' + Role + '] ' + Content);
end;

procedure TFRMOpenAIChatBot.ChatBotTranscription(Sender: TObject; var Text:
    string; var Accept: Boolean);
begin
  Accept := (Text <> '');
  DoLog('[user] ' + Text);

  if ContainsText(Text, 'inglÃ©s') or ContainsText(Text, 'ingles') or ContainsText(Text, 'english') then
  begin
    DoQuickConfiguration(0);
    Accept := False;
  end
  else if ContainsText(Text, 'italian') or ContainsText(Text, 'italiano') then
  begin
    DoQuickConfiguration(3);
    Accept := False;
  end
  else if ContainsText(Text, 'spanish') or ContainsText(Text, 'espaÃ±ol') then
  begin
    DoQuickConfiguration(4);
    Accept := False;
  end
  else if ContainsText(Text, 'stop') then
  begin
    Accept := False;
  end
  else if ContainsText(Text, 'exit') then
  begin
    DoApplicationExit;
    Accept := False;
  end;
end;

procedure TFRMOpenAIChatBot.Configuration1Click(Sender: TObject);
begin
  DoConfiguration;
end;

procedure TFRMOpenAIChatBot.DoConfiguration;
begin
  Visible := True;
end;

procedure TFRMOpenAIChatBot.DoApplicationExit;
begin
  Application.Terminate;
end;

procedure TFRMOpenAIChatBot.DoUpdateControlState(aListening: Boolean);
begin
  if Assigned(FFormControls) then
    FFormControls.Listening := aListening;
end;

procedure TFRMOpenAIChatBot.FormDestroy(Sender: TObject);
begin
  sgcTrayIcon.Visible := False;
  DoSaveSettings;
end;

procedure TFRMOpenAIChatBot.FormCreate(Sender: TObject);
begin
  Try
    // icon
    sgcTrayIcon.IconIndex := Ord(iconStop);
    sgcTrayIcon.Visible := True;
    // settings
    DoLoadSettings;
    // visible
    if txtAPIKey.Text = '' then
    begin
      pageMain.ActivePage := tabConfiguration;
      DoConfiguration;
    end
    else
    begin
      pageMain.ActivePage := tabLog;
      DoStart;
    end;
    DoShowControls;
  Except
    On E: Exception do
    begin
      MessageDlg('Initialization error: ' + E.Message, mtError,
      [mbOk], 0, mbOk);
      Application.Terminate;
    end;
  End;
end;

procedure TFRMOpenAIChatBot.DoLoadSettings;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    txtAPIKey.Text := oINI.ReadString('OPENAI', 'API_KEY', '');
    // speechtotext
    cboSpeechToTextLanguage.ItemIndex := oINI.ReadInteger('SPEECHTOTEXT',
      'Language', cboSpeechToTextLanguage.ItemIndex);
    txtSpeechToTextModel.Text := oINI.ReadString('SPEECHTOTEXT', 'Model',
      txtSpeechToTextModel.Text);
    txtSpeechToTextFilename.Text := oINI.ReadString('SPEECHTOTEXT', 'Filename',
      txtSpeechToTextFilename.Text);
    cboSpeechToTextCaptureAudio.ItemIndex := oINI.ReadInteger('SPEECHTOTEXT',
      'CaptureAudio', cboSpeechToTextCaptureAudio.ItemIndex);

    // texttospeech
    cboTextToSpeechProviders.ItemIndex := oINI.ReadInteger('TEXTTOSPEECH',
      'Provider', cboTextToSpeechProviders.ItemIndex);
    // google
    txtTextToSpeechGoogleSettings.Text := oINI.ReadString('TEXTTOSPEECH.GOOGLE',
      'Settings', txtTextToSpeechGoogleSettings.Text);
    cboTextToSpeechGoogleVoices.ItemIndex := oINI.ReadInteger('TEXTTOSPEECH.GOOGLE',
      'VoiceId', cboTextToSpeechGoogleVoices.ItemIndex);
    // amazon
    cboTextToSpeechAmazonVoices.ItemIndex :=
      oINI.ReadInteger('TEXTTOSPEECH.AMAZON', 'VoiceId',
      cboTextToSpeechAmazonVoices.ItemIndex);
    txtTextToSpeechAmazonAccessKey.Text :=
      oINI.ReadString('TEXTTOSPEECH.AMAZON', 'AccessKey',
      txtTextToSpeechAmazonAccessKey.Text);
    txtTextToSpeechAmazonSecretKey.Text :=
      oINI.ReadString('TEXTTOSPEECH.AMAZON', 'SecretKey',
      txtTextToSpeechAmazonSecretKey.Text);
    txtTextToSpeechAmazonRegion.Text := oINI.ReadString('TEXTTOSPEECH.AMAZON',
      'Region', txtTextToSpeechAmazonRegion.Text);
  Finally
    oINI.Free;
  End;
end;

procedure TFRMOpenAIChatBot.DoLog(const aText: string);
begin
  memoLog.Lines.Add(aText);
end;

procedure TFRMOpenAIChatBot.DoQuickConfiguration(aItemIndex: Integer = -1);
begin
  if aItemIndex > -1 then
    cboQuickConfiguration.ItemIndex := aItemIndex;

  case cboQuickConfiguration.ItemIndex of
    0: // english
      begin
        cboSpeechToTextLanguage.ItemIndex := 38;
        cboTextToSpeechGoogleVoices.ItemIndex := 90;
        cboTextToSpeechAmazonVoices.ItemIndex := 23;
        ChatBot.ChatAsSystem('Now you are my assistant and your name is Joanna.', True)
      end;
    1: // german
      begin
        cboSpeechToTextLanguage.ItemIndex := 51;
        cboTextToSpeechGoogleVoices.ItemIndex := 163;
        cboTextToSpeechAmazonVoices.ItemIndex := 43;
        ChatBot.ChatAsSystem('Jetzt bist du meine Assistentin und dein Name ist Vicki.', True)
      end;
    2: // french
      begin
        cboSpeechToTextLanguage.ItemIndex := 45;
        cboTextToSpeechGoogleVoices.ItemIndex := 147;
        cboTextToSpeechAmazonVoices.ItemIndex := 37;
        ChatBot.ChatAsSystem('Maintenant tu es mon assistant et ton nom est Mathieu..', True)
      end;
    3: // italian
      begin
        cboSpeechToTextLanguage.ItemIndex := 70;
        cboTextToSpeechGoogleVoices.ItemIndex := 215;
        cboTextToSpeechAmazonVoices.ItemIndex := 52;
        ChatBot.ChatAsSystem('Ora sei la mia assistente e ti chiami Bianca.', True)
      end;
    4: // spanish
      begin
        cboSpeechToTextLanguage.ItemIndex := 132;
        cboTextToSpeechGoogleVoices.ItemIndex := 348;
        cboTextToSpeechAmazonVoices.ItemIndex := 79;
        ChatBot.ChatAsSystem('Ahora eres mi asistente y tu nombre es Sergio.', True)
      end;
    5: // dutch
      begin
        cboSpeechToTextLanguage.ItemIndex := 36;
        cboTextToSpeechGoogleVoices.ItemIndex := 39;
        cboTextToSpeechAmazonVoices.ItemIndex := 7;
        ChatBot.ChatAsSystem('Nu ben je mijn assistent en je naam is Laura.', True)
      end;
    6: // polish
      begin
        cboSpeechToTextLanguage.ItemIndex := 112;
        cboTextToSpeechGoogleVoices.ItemIndex := 302;
        cboTextToSpeechAmazonVoices.ItemIndex := 66;
        ChatBot.ChatAsSystem('Teraz jesteÅ› mojÄ… asystentkÄ… i masz na imiÄ™ Ola.', True)
      end;
  end;
end;

procedure TFRMOpenAIChatBot.DoSaveSettings;
var
  oINI: TINIFile;
begin
  oINI := TINIFile.Create(ChangeFileExt(Application.ExeName, '.ini'));
  Try
    oINI.Writestring('OPENAI', 'API_KEY', txtAPIKey.Text);

    // speechtotext
    oINI.WriteInteger('SPEECHTOTEXT', 'Language',
      cboSpeechToTextLanguage.ItemIndex);
    oINI.Writestring('SPEECHTOTEXT', 'Model', txtSpeechToTextModel.Text);
    oINI.Writestring('SPEECHTOTEXT', 'Filename', txtSpeechToTextFilename.Text);
    oINI.WriteInteger('SPEECHTOTEXT', 'CaptureAudio',
      cboSpeechToTextCaptureAudio.ItemIndex);
    // texttospeech
    oINI.WriteInteger('TEXTTOSPEECH', 'Provider',
      cboTextToSpeechProviders.ItemIndex);
    // google
    oINI.WriteString('TEXTTOSPEECH.GOOGLE',
      'Settings', txtTextToSpeechGoogleSettings.Text);
    oINI.WriteInteger('TEXTTOSPEECH.GOOGLE',
      'VoiceId', cboTextToSpeechGoogleVoices.ItemIndex);
    // amazon
    oINI.WriteInteger('TEXTTOSPEECH.AMAZON', 'VoiceId',
      cboTextToSpeechAmazonVoices.ItemIndex);
    oINI.Writestring('TEXTTOSPEECH.AMAZON', 'AccessKey',
      txtTextToSpeechAmazonAccessKey.Text);
    oINI.Writestring('TEXTTOSPEECH.AMAZON', 'SecretKey',
      txtTextToSpeechAmazonSecretKey.Text);
    oINI.Writestring('TEXTTOSPEECH.AMAZON', 'Region',
      txtTextToSpeechAmazonRegion.Text);
  Finally
    oINI.Free;
  End;
end;

procedure TFRMOpenAIChatBot.DoShowControls;
begin
  if not Assigned(FFormControls) then
  begin
    FFormControls := TFRMOpenAIChatBot_Controls.Create(nil);
    FFormControls.OnControlStart := OnControlStartEvent;
    FFormControls.OnControlStop := OnControlStopEvent;
    FFormControls.OnControlConfiguration := OnControlConfigurationEvent;
    FFormControls.OnControlExit := OnControlExitEvent;
  end;
  FFormControls.Show;
end;

procedure TFRMOpenAIChatBot.DoStart;
begin
  // openai
  ChatBot.OpenAIOptions.ApiKey := txtAPIKey.Text;
  // speech to text
  ChatBot.ChatBotOptions.Transcription.Language := GetTranscriptionLanguage;
  ChatBot.ChatBotOptions.Transcription.Model := txtSpeechToTextModel.Text;
  AudioRecorderMCI.RecorderOptions.Filename :=
    txtSpeechToTextFilename.Text;
  AudioRecorderMCI.RecorderOptions.Mode := TsgcAudioRecorderMode(cboSpeechToTextCaptureAudio.ItemIndex);
  // text to speech
  case cboTextToSpeechProviders.ItemIndex of
    0:
      ChatBot.TextToSpeech := TextToSpeechSystem;
    1:
      begin
        if txtTextToSpeechGoogleSettings.Text <> '' then
          TextToSpeechGoogle.GoogleOptions.Settings.LoadFromFile(txtTextToSpeechGoogleSettings.Text);
        TextToSpeechGoogle.GoogleOptions.VoiceId := GetGoogleVoiceId;
        TextToSpeechGoogle.GoogleOptions.Gender := GetGoogleGender;
        TextToSpeechGoogle.GoogleOptions.Language := GetGoogleLanguage;
        ChatBot.TextToSpeech := TextToSpeechGoogle;
      end;
    2:
      begin
        TextToSpeechAmazon.AmazonOptions.AWSOptions.AccessKey :=
          txtTextToSpeechAmazonAccessKey.Text;
        TextToSpeechAmazon.AmazonOptions.AWSOptions.SecretKey :=
          txtTextToSpeechAmazonSecretKey.Text;
        TextToSpeechAmazon.AmazonOptions.AWSOptions.Region :=
          txtTextToSpeechAmazonRegion.Text;
        TextToSpeechAmazon.AmazonOptions.VoiceId := GetAmazonVoiceId;
        TextToSpeechAmazon.AmazonOptions.Engine := GetAmazonEngine;
        ChatBot.TextToSpeech := TextToSpeechAmazon;
      end;
  end;
  ChatBot.AudioRecorder := AudioRecorderMCI;
  ChatBot.Start;
end;

procedure TFRMOpenAIChatBot.DoStop;
begin
  ChatBot.Stop;
end;

procedure TFRMOpenAIChatBot.Exit1Click(Sender: TObject);
begin
  DoApplicationExit;
end;

procedure TFRMOpenAIChatBot.FormCloseQuery(Sender: TObject; var CanClose:
    Boolean);
begin
  CanClose := False;
  self.Visible := False;
end;

function TFRMOpenAIChatBot.GetAmazonVoiceId: string;
var
  oList: TStringList;
begin
  oList := TStringList.Create;
  Try
    oList.Delimiter := '_';
    oList.DelimitedText := cboTextToSpeechAmazonVoices.Text;
    Result := oList[0];
  Finally
    oList.Free;
  End;
end;

function TFRMOpenAIChatBot.GetAmazonEngine: string;
var
  oList: TStringList;
begin
  oList := TStringList.Create;
  Try
    oList.Delimiter := '_';
    oList.DelimitedText := cboTextToSpeechAmazonVoices.Text;
    Result := oList[3];
    if UpperCase(Result) = 'YES' then
      Result := 'neural'
    else
      Result := 'standard';
  Finally
    oList.Free;
  End;
end;

function TFRMOpenAIChatBot.GetGoogleGender: string;
var
  oList: TStringList;
begin
  oList := TStringList.Create;
  Try
    oList.Delimiter := '_';
    oList.DelimitedText := cboTextToSpeechGoogleVoices.Text;
    Result := oList[2];
  Finally
    oList.Free;
  End;
end;

function TFRMOpenAIChatBot.GetGoogleLanguage: string;
var
  oList: TStringList;
begin
  oList := TStringList.Create;
  Try
    oList.Delimiter := '_';
    oList.DelimitedText := cboTextToSpeechGoogleVoices.Text;
    Result := oList[1];
  Finally
    oList.Free;
  End;
end;

function TFRMOpenAIChatBot.GetGoogleVoiceId: string;
var
  oList: TStringList;
begin
  oList := TStringList.Create;
  Try
    oList.Delimiter := '_';
    oList.DelimitedText := cboTextToSpeechGoogleVoices.Text;
    Result := oList[0];
  Finally
    oList.Free;
  End;
end;

function TFRMOpenAIChatBot.GetTranscriptionLanguage: string;
begin
  Result := LeftStr(cboSpeechToTextLanguage.Text, 2);
end;

procedure TFRMOpenAIChatBot.OnControlConfigurationEvent(Sender: TObject);
begin
  DoConfiguration;
end;

procedure TFRMOpenAIChatBot.OnControlExitEvent(Sender: TObject);
begin
  DoApplicationExit;
end;

procedure TFRMOpenAIChatBot.OnControlStartEvent(Sender: TObject);
begin
  DoStart;
end;

procedure TFRMOpenAIChatBot.OnControlStopEvent(Sender: TObject);
begin
  DoStop;
end;

procedure TFRMOpenAIChatBot.Start1Click(Sender: TObject);
begin
  DoStart;
end;

procedure TFRMOpenAIChatBot.Stop1Click(Sender: TObject);
begin
  DoStop;
end;

end.
```

