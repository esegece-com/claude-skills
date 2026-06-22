# TsgcAudioRecorderWave

unit: sgcAI
Edition: Enterprise

Add `sgcAI` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `WaveOptions: TsgcAudioRecorderWave_Options` | [TsgcAudioRecorderWave_Options](../types/TsgcAudioRecorderWave_Options.md) | `__property TsgcAudioRecorderWave_Options * WaveOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnAudio: TsgcOnAudioStreamEvent` | [TsgcOnAudioStreamEvent](../types/TsgcOnAudioStreamEvent.md) | `__property TsgcOnAudioStreamEvent OnAudio;` |
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

