# TsgcAIOpenAIChatBot

unit: sgcAI
Edition: Enterprise

Add `sgcAI` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `TextToSpeech: TsgcTextToSpeech` | [TsgcTextToSpeech](../types/TsgcTextToSpeech.md) | `__property TsgcTextToSpeech * TextToSpeech;` |
| `AudioRecorder: TsgcAudioRecorder` | [TsgcAudioRecorder](../types/TsgcAudioRecorder.md) | `__property TsgcAudioRecorder * AudioRecorder;` |
| `Embeddings: TsgcAI_OpenAI_Embeddings` | [TsgcAI_OpenAI_Embeddings](../types/TsgcAI_OpenAI_Embeddings.md) | `__property TsgcAI_OpenAI_Embeddings * Embeddings;` |
| `OpenAIOptions: TsgcHTTPOpenAI_Options` | [TsgcHTTPOpenAI_Options](../types/TsgcHTTPOpenAI_Options.md) | `__property TsgcHTTPOpenAI_Options * OpenAIOptions;` |
| `ChatBotOptions: TsgcHTTPOpenAIChatBot_Options` | [TsgcHTTPOpenAIChatBot_Options](../types/TsgcHTTPOpenAIChatBot_Options.md) | `__property TsgcHTTPOpenAIChatBot_Options * ChatBotOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `SpeechToText: TsgcSpeechToText` | [TsgcSpeechToText](../types/TsgcSpeechToText.md) | `__property TsgcSpeechToText * SpeechToText;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnAudioStart: TsgcOpenAIAudioStart` | [TsgcOpenAIAudioStart](../types/TsgcOpenAIAudioStart.md) | `__property TsgcOpenAIAudioStart * OnAudioStart;` |
| `OnAudioStop: TsgcOpenAIAudioStop` | [TsgcOpenAIAudioStop](../types/TsgcOpenAIAudioStop.md) | `__property TsgcOpenAIAudioStop * OnAudioStop;` |
| `OnChatCompletion: TsgcOpenAIChatCompletion` | [TsgcOpenAIChatCompletion](../types/TsgcOpenAIChatCompletion.md) | `__property TsgcOpenAIChatCompletion * OnChatCompletion;` |
| `OnTranscription: TsgcOpenAITranscription` | [TsgcOpenAITranscription](../types/TsgcOpenAITranscription.md) | `__property TsgcOpenAITranscription * OnTranscription;` |

## Methods

Delphi

```pascal
procedure ChatAsUser(const aPrompt: string; aHistory: TsgcOpenAIArray_Request_Completion_Messages = nil);
procedure ChatAsSystem(const aText: string; aTextToSpeech: Boolean = False; aHistory: TsgcOpenAIArray_Request_Completion_Messages = nil);
function GetEmbedding(const aPrompt: string; const aParams: string = ''): string;
procedure Start;
procedure Stop;
```

C++Builder

```cpp
void __fastcall ChatAsUser(const UnicodeString aPrompt, TsgcOpenAIArray_Request_Completion_Messages * aHistory = nil);
void __fastcall ChatAsSystem(const UnicodeString aText, bool aTextToSpeech = False, TsgcOpenAIArray_Request_Completion_Messages * aHistory = nil);
UnicodeString __fastcall GetEmbedding(const UnicodeString aPrompt, const UnicodeString aParams = '');
void __fastcall Start();
void __fastcall Stop();
```

