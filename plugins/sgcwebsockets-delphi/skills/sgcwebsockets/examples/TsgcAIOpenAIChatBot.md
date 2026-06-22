# TsgcAIOpenAIChatBot - Example

Usage of `TsgcAIOpenAIChatBot` extracted from the **15.AI/02.Applications/01.ChatBot** demo. See the full project for context.

API reference: [TsgcAIOpenAIChatBot](../reference/api/TsgcAIOpenAIChatBot.md)
Source demo: `15.AI/02.Applications/01.ChatBot` (file `fOpenAIChatBot.pas`)

```pascal
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
  ChatBot.ChatAsSystem('Teraz jesteś moją asystentką i masz na imię Ola.', True)
  end;
  end;

ChatBot.OpenAIOptions.ApiKey := txtAPIKey.Text;
ChatBot.ChatBotOptions.Transcription.Language := GetTranscriptionLanguage;
ChatBot.ChatBotOptions.Transcription.Model := txtSpeechToTextModel.Text;
```

