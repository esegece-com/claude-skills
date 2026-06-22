# TsgcAIOpenAITranslator - Example

Usage of `TsgcAIOpenAITranslator` extracted from the **15.AI/02.Applications/02.Translator** demo. See the full project for context.

API reference: [TsgcAIOpenAITranslator](../reference/api/TsgcAIOpenAITranslator.md)
Source demo: `15.AI/02.Applications/02.Translator` (file `fOpenAITranslator.pas`)

```pascal
procedure TFRMOpenAITranslator.chkTextToSpeechClick(Sender: TObject);
  begin
  if not chkTextToSpeech.Checked then
  Translator.TextToSpeech := nil;
  end;

Translator.OpenAIOptions.ApiKey := txtAPIKey.Text;
Translator.TranslatorOptions.Translation.Model := txtSpeechToTextModel.Text;
Translator.TextToSpeech := TextToSpeechSystem;
Translator.TextToSpeech := TextToSpeechGoogle;
Translator.TextToSpeech := TextToSpeechAmazon;
Translator.TextToSpeech := nil;
Translator.AudioRecorder := AudioRecorderMCI;
Translator.Start;
procedure TFRMOpenAITranslator.Start1Click(Sender: TObject);
```

