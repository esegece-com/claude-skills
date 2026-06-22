# TsgcAIOpenAIAssistant

unit: sgcAI
Edition: Enterprise

Add `sgcAI` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `TextToSpeech: TsgcTextToSpeech` | [TsgcTextToSpeech](../types/TsgcTextToSpeech.md) | `__property TsgcTextToSpeech * TextToSpeech;` |
| `AudioRecorder: TsgcAudioRecorder` | [TsgcAudioRecorder](../types/TsgcAudioRecorder.md) | `__property TsgcAudioRecorder * AudioRecorder;` |
| `OpenAIOptions: TsgcHTTPOpenAI_Options` | [TsgcHTTPOpenAI_Options](../types/TsgcHTTPOpenAI_Options.md) | `__property TsgcHTTPOpenAI_Options * OpenAIOptions;` |
| `AssistantOptions: TsgcAI_OpenAI_Assistant_Options` | [TsgcAI_OpenAI_Assistant_Options](../types/TsgcAI_OpenAI_Assistant_Options.md) | `__property TsgcAI_OpenAI_Assistant_Options * AssistantOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `SpeechToText: TsgcSpeechToText` | [TsgcSpeechToText](../types/TsgcSpeechToText.md) | `__property TsgcSpeechToText * SpeechToText;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnAudioStart: TsgcOpenAIAudioStart` | [TsgcOpenAIAudioStart](../types/TsgcOpenAIAudioStart.md) | `__property TsgcOpenAIAudioStart * OnAudioStart;` |
| `OnAudioStop: TsgcOpenAIAudioStop` | [TsgcOpenAIAudioStop](../types/TsgcOpenAIAudioStop.md) | `__property TsgcOpenAIAudioStop * OnAudioStop;` |
| `OnStreamMessage: TsgcOpenAIStreamMessage` | [TsgcOpenAIStreamMessage](../types/TsgcOpenAIStreamMessage.md) | `__property TsgcOpenAIStreamMessage * OnStreamMessage;` |
| `OnStreamMessageDelta: TsgcOpenAIStreamMessageDelta` | [TsgcOpenAIStreamMessageDelta](../types/TsgcOpenAIStreamMessageDelta.md) | `__property TsgcOpenAIStreamMessageDelta * OnStreamMessageDelta;` |
| `OnStreamRun: TsgcOpenAIStreamRun` | [TsgcOpenAIStreamRun](../types/TsgcOpenAIStreamRun.md) | `__property TsgcOpenAIStreamRun * OnStreamRun;` |
| `OnStreamError: TsgcOpenAIStreamError` | [TsgcOpenAIStreamError](../types/TsgcOpenAIStreamError.md) | `__property TsgcOpenAIStreamError * OnStreamError;` |
| `OnStreamDone: TsgcOpenAIStreamDone` | [TsgcOpenAIStreamDone](../types/TsgcOpenAIStreamDone.md) | `__property TsgcOpenAIStreamDone * OnStreamDone;` |
| `OnFunctionCall: TsgcOpenAIFunctionCall` | [TsgcOpenAIFunctionCall](../types/TsgcOpenAIFunctionCall.md) | `__property TsgcOpenAIFunctionCall * OnFunctionCall;` |

## Methods

Delphi

```pascal
function CreateAssistant: TsgcOpenAIClass_Assistant;
function GetAssistant(const aAssistantId: string) : TsgcOpenAIClass_Assistant;
function ListAssistants: TsgcOpenAIClass_Response_List_Assistants;
function CreateThread: TsgcOpenAIClass_Thread;
function GetThread(const aThreadId: string): TsgcOpenAIClass_Thread;
function UploadVectorStoreFile(const aVectorStoreName, aFilename: string): Boolean;
function GetVectorStoreFiles(const aVectorStoreName: string) : TsgcOpenAIClass_Response_List_VectorStoreFiles;
function CreateMessageText(const aThreadId, aText: string; const aRole: string = 'user'): TsgcOpenAIClass_Message;
function GetMessages(const aThreadId: string; aRunId: string; const aLimit: Integer = 20; aOrder: string = 'desc'; aAfter: string = ''; aBefore: string = ''): TsgcOpenAIClass_Response_List_Messages;
function CreateRun(const aThreadId: string; aStream: Boolean = False) : TsgcOpenAIClass_Run;
function GetRun(const aThreadId, aRunId: string): TsgcOpenAIClass_Run;
function CreateRunAndWait(const aThreadId: string; aTimeout: Integer = 30000; aStream: Boolean = False): TsgcOpenAIClass_Run;
procedure Start;
procedure Stop;
```

C++Builder

```cpp
TsgcOpenAIClass_Assistant * __fastcall CreateAssistant();
TsgcOpenAIClass_Assistant * __fastcall GetAssistant(const UnicodeString aAssistantId);
TsgcOpenAIClass_Response_List_Assistants * __fastcall ListAssistants();
TsgcOpenAIClass_Thread * __fastcall CreateThread();
TsgcOpenAIClass_Thread * __fastcall GetThread(const UnicodeString aThreadId);
bool __fastcall UploadVectorStoreFile(const UnicodeString aVectorStoreName, const UnicodeString aFilename);
TsgcOpenAIClass_Response_List_VectorStoreFiles * __fastcall GetVectorStoreFiles(const UnicodeString aVectorStoreName);
TsgcOpenAIClass_Message * __fastcall CreateMessageText(const UnicodeString aThreadId, const UnicodeString aText, const UnicodeString aRole = 'user');
TsgcOpenAIClass_Response_List_Messages * __fastcall GetMessages(const UnicodeString aThreadId, UnicodeString aRunId, const int aLimit = 20, UnicodeString aOrder = 'desc', UnicodeString aAfter = '', UnicodeString aBefore = '');
TsgcOpenAIClass_Run * __fastcall CreateRun(const UnicodeString aThreadId, bool aStream = False);
TsgcOpenAIClass_Run * __fastcall GetRun(const UnicodeString aThreadId, const UnicodeString aRunId);
TsgcOpenAIClass_Run * __fastcall CreateRunAndWait(const UnicodeString aThreadId, int aTimeout = 30000, bool aStream = False);
void __fastcall Start();
void __fastcall Stop();
```

