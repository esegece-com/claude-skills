# TsgcAudioRecorderMCI

unit: sgcAI
Edition: Enterprise

Add `sgcAI` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `MCIOptions: TsgcAudioRecorderMCI_Options` | [TsgcAudioRecorderMCI_Options](../types/TsgcAudioRecorderMCI_Options.md) | `__property TsgcAudioRecorderMCI_Options * MCIOptions;` |
| `RecorderOptions: TsgcAudioRecorderOptions` | [TsgcAudioRecorderOptions](../types/TsgcAudioRecorderOptions.md) | `__property TsgcAudioRecorderOptions * RecorderOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnAudio: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnAudio;` |
| `OnStart: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnStart;` |
| `OnStop: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnStop;` |

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

