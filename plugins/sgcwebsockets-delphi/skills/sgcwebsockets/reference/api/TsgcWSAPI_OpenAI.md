# TsgcWSAPI_OpenAI

unit: sgcWebSocket_APIs
Edition: requires SGC_AI

Add `sgcWebSocket_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `OpenAIOptions: TsgcWS_API_OpenAI_Options` | [TsgcWS_API_OpenAI_Options](../types/TsgcWS_API_OpenAI_Options.md) | `__property TsgcWS_API_OpenAI_Options * OpenAIOptions;` |
| `AudioRecorder: TsgcAudioRecorderStreaming` | [TsgcAudioRecorderStreaming](../types/TsgcAudioRecorderStreaming.md) | `__property TsgcAudioRecorderStreaming * AudioRecorder;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `URL: String (read-only)` | `String` | `__property UnicodeString URL /* read-only */;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |
| `OnAudioStart: TsgcOpenAIAudioStart` | [TsgcOpenAIAudioStart](../types/TsgcOpenAIAudioStart.md) | `__property TsgcOpenAIAudioStart * OnAudioStart;` |
| `OnAudioStop: TsgcOpenAIAudioStop` | [TsgcOpenAIAudioStop](../types/TsgcOpenAIAudioStop.md) | `__property TsgcOpenAIAudioStop * OnAudioStop;` |
| `OnOpenAIEvent: TsgcWSOnOpenAIEvent` | [TsgcWSOnOpenAIEvent](../types/TsgcWSOnOpenAIEvent.md) | `__property TsgcWSOnOpenAIEvent OnOpenAIEvent;` |
| `OnOpenAIError: TsgcWSOnOpenAIError` | [TsgcWSOnOpenAIError](../types/TsgcWSOnOpenAIError.md) | `__property TsgcWSOnOpenAIError OnOpenAIError;` |
| `OnOpenAIAudioTranscriptionDelta: TsgcWSOnOpenAIAudioTranscriptionDelta` | [TsgcWSOnOpenAIAudioTranscriptionDelta](../types/TsgcWSOnOpenAIAudioTranscriptionDelta.md) | `__property TsgcWSOnOpenAIAudioTranscriptionDelta OnOpenAIAudioTranscriptionDelta;` |
| `OnOpenAIAudioTranscriptionCompleted: TsgcWSOnOpenAIAudioTranscriptionCompleted` | [TsgcWSOnOpenAIAudioTranscriptionCompleted](../types/TsgcWSOnOpenAIAudioTranscriptionCompleted.md) | `__property TsgcWSOnOpenAIAudioTranscriptionCompleted OnOpenAIAudioTranscriptionCompleted;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |

## Methods

Delphi

```pascal
procedure AppendInputAudioBuffer(const aStream: TStream);
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall AppendInputAudioBuffer(const TStream * aStream);
void __fastcall QueueClear();
```

