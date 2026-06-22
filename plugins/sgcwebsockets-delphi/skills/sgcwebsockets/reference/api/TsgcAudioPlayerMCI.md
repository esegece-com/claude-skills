# TsgcAudioPlayerMCI

unit: sgcAI
Edition: Enterprise

Add `sgcAI` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnStart: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnStart;` |
| `OnStop: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnStop;` |

## Methods

Delphi

```pascal
procedure Play(const aFileName: String);
```

C++Builder

```cpp
void __fastcall Play(const UnicodeString aFileName);
```

