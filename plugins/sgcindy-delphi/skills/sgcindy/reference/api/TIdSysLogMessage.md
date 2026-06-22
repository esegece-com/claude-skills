# TIdSysLogMessage

unit: IdSysLogMessage

Add `IdSysLogMessage` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `RawMessage: string` | `string` | `__property UnicodeString RawMessage;` |
| `Peer: string` | `string` | `__property UnicodeString Peer;` |
| `TimeStamp: TDateTime` | `TDateTime` | `__property System::TDateTime TimeStamp;` |
| `Pri: TIdSyslogPRI` | `TIdSyslogPRI` | `__property TIdSyslogPRI * Pri;` |
| `Facility: TidSyslogFacility` | [TidSyslogFacility](../types/TidSyslogFacility.md) | `__property TidSyslogFacility * Facility;` |
| `Severity: TIdSyslogSeverity` | [TIdSyslogSeverity](../types/TIdSyslogSeverity.md) | `__property TIdSyslogSeverity * Severity;` |
| `Hostname: string` | `string` | `__property UnicodeString Hostname;` |
| `Msg: TIdSysLogMsgPart` | [TIdSysLogMsgPart](../types/TIdSysLogMsgPart.md) | `__property TIdSysLogMsgPart * Msg;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure Assign(Source: TPersistent);
function EncodeMessage: String;
procedure ReadFromBytes(const ASrc: TIdBytes; const APeer : String);
procedure SendToHost(const Dest: String);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Assign(TPersistent * Source);
UnicodeString __fastcall EncodeMessage();
void __fastcall ReadFromBytes(const TIdBytes * ASrc, const UnicodeString APeer);
void __fastcall SendToHost(const UnicodeString Dest);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

