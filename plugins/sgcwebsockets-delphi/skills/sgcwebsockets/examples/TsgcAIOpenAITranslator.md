# TsgcAIOpenAITranslator - Example

Full source of `fOpenAITranslator.pas` from the **15.AI/02.Applications/02.Translator** demo, which uses `TsgcAIOpenAITranslator`.

API reference: [TsgcAIOpenAITranslator](../reference/api/TsgcAIOpenAITranslator.md)
Source demo: `15.AI/02.Applications/02.Translator` (file `fOpenAITranslator.pas`)

```pascal
ï»¿unit fOpenAITranslator;

interface

uses
  Windows, Messages, SysUtils, Variants, Classes, Graphics,
  Controls, Forms, Dialogs, StdCtrls, ExtCtrls, ComCtrls,
  ImgList, Menus, ImageList, UITypes,
  // sgc
  sgcAI, fOpenAITranslator_Controls, sgcAI_OpenAI, sgcAI_OpenAI_Audio,
  sgcAI_OpenAI_Audio_Translator, sgcAI_AudioPlayer, sgcAI_AudioPlayer_MCI,
  sgcAI_TextToSpeech_Amazon, sgcAI_TextToSpeech_Google, sgcAI_TextToSpeech,
  sgcAI_TextToSpeech_System, sgcBase_Classes, sgcAI_AudioRecorder,
  sgcAI_AudioRecorder_MCI;

type
  TsgcTranslatorIcons = (iconPlay, iconStop);

  TFRMOpenAITranslator = class(TForm)
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
    cboSpeechToTextAudioRecorder: TComboBox;
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
    chkTextToSpeech: TCheckBox;
    AudioRecorderMCI: TsgcAudioRecorderMCI;
    TextToSpeechSystem: TsgcTextToSpeechSystem;
    TextToSpeechGoogle: TsgcTextToSpeechGoogle;
    TextToSpeechAmazon: TsgcTextToSpeechAmazon;
    AudioPlayerMCI: TsgcAudioPlayerMCI;
    Translator: TsgcAIOpenAITranslator;
    procedure cboQuickConfigurationChange(Sender: TObject);
    procedure cboTextToSpeechProvidersChange(Sender: TObject);
    procedure chkTextToSpeechClick(Sender: TObject);
    procedure Configuration1Click(Sender: TObject);
    procedure Exit1Click(Sender: TObject);
    procedure FormCloseQuery(Sender: TObject; var CanClose: Boolean);
    procedure FormDestroy(Sender: TObject);
    procedure FormCreate(Sender: TObject);
    procedure Start1Click(Sender: TObject);
    procedure Stop1Click(Sender: TObject);
    procedure TranslatorAudioStart(Sender: TObject);
    procedure TranslatorAudioStop(Sender: TObject);
    procedure TranslatorTranslation(Sender: TObject; var Text: string; var Accept:
        Boolean);
  private
    procedure DoLog(const aText: string);
  private
    function GetAmazonVoiceId: string;
    function GetAmazonEngine: string;
    function GetGoogleVoiceId: string;
    function GetGoogleLanguage: string;
    function GetGoogleGender: string;
  private
    procedure DoLoadSettings;
    procedure DoSaveSettings;
  protected
    procedure DoQuickConfiguration(aItemIndex: Integer = -1); virtual;
  protected
    FListening: Boolean;
    procedure DoStart; virtual;
    procedure DoStop; virtual;
    procedure DoConfiguration; virtual;
    procedure DoExitApplication; virtual;
  protected
    FFormControls: TFRMOpenAITranslator_Controls;
    procedure OnControlStartEvent(Sender: TObject); virtual;
    procedure OnControlStopEvent(Sender: TObject); virtual;
    procedure OnControlConfigurationEvent(Sender: TObject); virtual;
    procedure OnControlExitEvent(Sender: TObject); virtual;
    procedure DoUpdateControlState(aListening: Boolean); virtual;
    procedure DoUpdateControlTranslation(const aText: string); virtual;
    procedure DoShowControls; virtual;
  end;

var
  FRMOpenAITranslator: TFRMOpenAITranslator;

implementation

{$R *.dfm}

uses
  INIFiles, StrUtils;

procedure TFRMOpenAITranslator.cboQuickConfigurationChange(Sender: TObject);
begin
  if FListening then
    DoStop;

  DoQuickConfiguration;
end;

procedure TFRMOpenAITranslator.cboTextToSpeechProvidersChange(Sender: TObject);
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

procedure TFRMOpenAITranslator.chkTextToSpeechClick(Sender: TObject);
begin
  if not chkTextToSpeech.Checked then
    Translator.TextToSpeech := nil;
end;

procedure TFRMOpenAITranslator.Configuration1Click(Sender: TObject);
begin
  DoConfiguration;
end;

procedure TFRMOpenAITranslator.DoConfiguration;
begin
  Visible := True;
end;

procedure TFRMOpenAITranslator.DoExitApplication;
begin
  Application.Terminate;
end;

procedure TFRMOpenAITranslator.DoUpdateControlState(aListening: Boolean);
begin
  if Assigned(FFormControls) then
    FFormControls.Listening := aListening;
end;

procedure TFRMOpenAITranslator.FormDestroy(Sender: TObject);
begin
  sgcTrayIcon.Visible := False;
  DoSaveSettings;
end;

procedure TFRMOpenAITranslator.FormCreate(Sender: TObject);
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
      MessageDlg('Initialization error: ' + E.Message, mtError, [mbOk],
        0, mbOk);
      Application.Terminate;
    end;
  End;
end;

procedure TFRMOpenAITranslator.DoLoadSettings;
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
    cboSpeechToTextAudioRecorder.ItemIndex := oINI.ReadInteger('SPEECHTOTEXT',
      'AudioRecorder', cboSpeechToTextAudioRecorder.ItemIndex);

    // texttospeech
    chkTextToSpeech.Checked := oINI.ReadBool('TEXTTOSPEECH', 'Enabled',
      chkTextToSpeech.Checked);
    cboTextToSpeechProviders.ItemIndex := oINI.ReadInteger('TEXTTOSPEECH',
      'Provider', cboTextToSpeechProviders.ItemIndex);
    // google
    txtTextToSpeechGoogleSettings.Text := oINI.ReadString('TEXTTOSPEECH.GOOGLE',
      'Settings', txtTextToSpeechGoogleSettings.Text);
    cboTextToSpeechGoogleVoices.ItemIndex :=
      oINI.ReadInteger('TEXTTOSPEECH.GOOGLE', 'VoiceId',
      cboTextToSpeechGoogleVoices.ItemIndex);
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

procedure TFRMOpenAITranslator.DoLog(const aText: string);
begin
  memoLog.Lines.Add(aText);
end;

procedure TFRMOpenAITranslator.DoQuickConfiguration(aItemIndex: Integer = -1);
begin
  if aItemIndex > -1 then
    cboQuickConfiguration.ItemIndex := aItemIndex;

  case cboQuickConfiguration.ItemIndex of
    0: // english
      begin
        cboSpeechToTextLanguage.ItemIndex := 38;
      end;
    1: // german
      begin
        cboSpeechToTextLanguage.ItemIndex := 51;
      end;
    2: // french
      begin
        cboSpeechToTextLanguage.ItemIndex := 45;
      end;
    3: // italian
      begin
        cboSpeechToTextLanguage.ItemIndex := 70;
      end;
    4: // spanish
      begin
        cboSpeechToTextLanguage.ItemIndex := 132;
      end;
    5: // dutch
      begin
        cboSpeechToTextLanguage.ItemIndex := 36;
      end;
    6: // polish
      begin
        cboSpeechToTextLanguage.ItemIndex := 112;
      end;
  end;
end;

procedure TFRMOpenAITranslator.DoSaveSettings;
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
    oINI.WriteInteger('SPEECHTOTEXT', 'AudioRecorder',
      cboSpeechToTextAudioRecorder.ItemIndex);
    // texttospeech
    oINI.WriteInteger('TEXTTOSPEECH', 'Provider',
      cboTextToSpeechProviders.ItemIndex);
    oINI.WriteBool('TEXTTOSPEECH', 'Enabled', chkTextToSpeech.Checked);
    // google
    oINI.Writestring('TEXTTOSPEECH.GOOGLE', 'Settings',
      txtTextToSpeechGoogleSettings.Text);
    oINI.WriteInteger('TEXTTOSPEECH.GOOGLE', 'VoiceId',
      cboTextToSpeechGoogleVoices.ItemIndex);
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

procedure TFRMOpenAITranslator.DoShowControls;
begin
  if not Assigned(FFormControls) then
  begin
    FFormControls := TFRMOpenAITranslator_Controls.Create(nil);
    FFormControls.OnControlStart := OnControlStartEvent;
    FFormControls.OnControlStop := OnControlStopEvent;
    FFormControls.OnControlConfiguration := OnControlConfigurationEvent;
    FFormControls.OnControlExit := OnControlExitEvent;
  end;
  FFormControls.Show;
end;

procedure TFRMOpenAITranslator.DoStart;
begin
  // openai
  Translator.OpenAIOptions.ApiKey := txtAPIKey.Text;
  // speech to text
  Translator.TranslatorOptions.Translation.Model := txtSpeechToTextModel.Text;
  AudioRecorderMCI.RecorderOptions.Filename :=
    txtSpeechToTextFilename.Text;
  AudioRecorderMCI.RecorderOptions.Mode :=
    TsgcAudioRecorderMode(cboSpeechToTextAudioRecorder.ItemIndex);
  // text to speech
  if chkTextToSpeech.Checked then
  begin
    case cboTextToSpeechProviders.ItemIndex of
      0:
        Translator.TextToSpeech := TextToSpeechSystem;
      1:
        begin
          if txtTextToSpeechGoogleSettings.Text <> '' then
            TextToSpeechGoogle.GoogleOptions.Settings.LoadFromFile
              (txtTextToSpeechGoogleSettings.Text);
          TextToSpeechGoogle.GoogleOptions.VoiceId := GetGoogleVoiceId;
          TextToSpeechGoogle.GoogleOptions.Gender := GetGoogleGender;
          TextToSpeechGoogle.GoogleOptions.Language := GetGoogleLanguage;
          Translator.TextToSpeech := TextToSpeechGoogle;
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

          Translator.TextToSpeech := TextToSpeechAmazon;
        end;
    end;
  end
  else
    Translator.TextToSpeech := nil;
  Translator.AudioRecorder := AudioRecorderMCI;

  Translator.Start;
end;

procedure TFRMOpenAITranslator.DoStop;
begin
  Translator.Stop;
end;

procedure TFRMOpenAITranslator.DoUpdateControlTranslation(const aText: string);
begin
  if Assigned(FFormControls) then
    FFormControls.Translation := aText;
end;

procedure TFRMOpenAITranslator.Exit1Click(Sender: TObject);
begin
  DoExitApplication;
end;

procedure TFRMOpenAITranslator.FormCloseQuery(Sender: TObject;
  var CanClose: Boolean);
begin
  CanClose := False;
  self.Visible := False;
end;

function TFRMOpenAITranslator.GetAmazonVoiceId: string;
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

function TFRMOpenAITranslator.GetAmazonEngine: string;
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

function TFRMOpenAITranslator.GetGoogleGender: string;
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

function TFRMOpenAITranslator.GetGoogleLanguage: string;
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

function TFRMOpenAITranslator.GetGoogleVoiceId: string;
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

procedure TFRMOpenAITranslator.OnControlConfigurationEvent(Sender: TObject);
begin
  DoConfiguration;
end;

procedure TFRMOpenAITranslator.OnControlExitEvent(Sender: TObject);
begin
  DoExitApplication;
end;

procedure TFRMOpenAITranslator.OnControlStartEvent(Sender: TObject);
begin
  DoStart;
end;

procedure TFRMOpenAITranslator.OnControlStopEvent(Sender: TObject);
begin
  DoStop;
end;

procedure TFRMOpenAITranslator.Start1Click(Sender: TObject);
begin
  DoStart;
end;

procedure TFRMOpenAITranslator.Stop1Click(Sender: TObject);
begin
  DoStop;
end;

procedure TFRMOpenAITranslator.TranslatorAudioStart(Sender: TObject);
begin
  FListening := True;
  DoUpdateControlState(True);
  DoLog('#audio start');
  sgcTrayIcon.IconIndex := Ord(iconPlay);
end;

procedure TFRMOpenAITranslator.TranslatorAudioStop(Sender: TObject);
begin
  FListening := False;
  DoUpdateControlState(False);
  sgcTrayIcon.IconIndex := Ord(iconStop);
  DoLog('#audio stop');
end;

procedure TFRMOpenAITranslator.TranslatorTranslation(Sender: TObject; var Text:
    string; var Accept: Boolean);
begin
  DoUpdateControlTranslation(Text);
  DoLog('[translation] ' + Text);
end;

end.
```

