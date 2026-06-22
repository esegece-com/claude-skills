# TsgcAIOpenAITranslator

unit: sgcAI
Edition: Enterprise

Add `sgcAI` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `TextToSpeech: TsgcTextToSpeech` | [TsgcTextToSpeech](../types/TsgcTextToSpeech.md) | `__property TsgcTextToSpeech * TextToSpeech;` |
| `AudioRecorder: TsgcAudioRecorder` | [TsgcAudioRecorder](../types/TsgcAudioRecorder.md) | `__property TsgcAudioRecorder * AudioRecorder;` |
| `OpenAIOptions: TsgcHTTPOpenAI_Options` | [TsgcHTTPOpenAI_Options](../types/TsgcHTTPOpenAI_Options.md) | `__property TsgcHTTPOpenAI_Options * OpenAIOptions;` |
| `TranslatorOptions: TsgcHTTPOpenAITranslator_Options` | [TsgcHTTPOpenAITranslator_Options](../types/TsgcHTTPOpenAITranslator_Options.md) | `__property TsgcHTTPOpenAITranslator_Options * TranslatorOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `SpeechToText: TsgcSpeechToText` | [TsgcSpeechToText](../types/TsgcSpeechToText.md) | `__property TsgcSpeechToText * SpeechToText;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnAudioStart: TsgcOpenAIAudioStart` | [TsgcOpenAIAudioStart](../types/TsgcOpenAIAudioStart.md) | `__property TsgcOpenAIAudioStart * OnAudioStart;` |
| `OnAudioStop: TsgcOpenAIAudioStop` | [TsgcOpenAIAudioStop](../types/TsgcOpenAIAudioStop.md) | `__property TsgcOpenAIAudioStop * OnAudioStop;` |
| `OnTranslation: TsgcOpenAITranslation` | [TsgcOpenAITranslation](../types/TsgcOpenAITranslation.md) | `__property TsgcOpenAITranslation * OnTranslation;` |

## Methods

Delphi

```pascal
procedure Start;
procedure Stop;
```

C++Builder

```cpp
void __fastcall Start();
void __fastcall Stop();
```

