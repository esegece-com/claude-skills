# TsgcSTUNClient

unit: sgcP2P
Edition: requires SGC_STUN

Add `sgcP2P` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Host: string` | `string` | `__property UnicodeString Host;` |
| `Port: Integer` | `Integer` | `__property int Port;` |
| `IPVersion: TIdIPVersion` | `TIdIPVersion` | `__property TIdIPVersion * IPVersion;` |
| `RetransmissionOptions: TsgcSTUNPRetransmissionClient_Options` | [TsgcSTUNPRetransmissionClient_Options](../types/TsgcSTUNPRetransmissionClient_Options.md) | `__property TsgcSTUNPRetransmissionClient_Options * RetransmissionOptions;` |
| `STUNOptions: TsgcSTUNClient_Options` | [TsgcSTUNClient_Options](../types/TsgcSTUNClient_Options.md) | `__property TsgcSTUNClient_Options * STUNOptions;` |
| `Transport: TsgcStunTransport` | [TsgcStunTransport](../types/TsgcStunTransport.md) | `__property TsgcStunTransport * Transport;` |
| `LogFile: TsgcSTUNLogFile` | [TsgcSTUNLogFile](../types/TsgcSTUNLogFile.md) | `__property TsgcSTUNLogFile * LogFile;` |
| `NotifyEvents: TwsNotifyEvent` | [TwsNotifyEvent](../types/TwsNotifyEvent.md) | `__property TwsNotifyEvent NotifyEvents;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnSTUNException: TsgcSTUNExceptionEvent` | [TsgcSTUNExceptionEvent](../types/TsgcSTUNExceptionEvent.md) | `__property TsgcSTUNExceptionEvent OnSTUNException;` |
| `OnSTUNResponseError: TsgcSTUNResponseErrorEvent` | [TsgcSTUNResponseErrorEvent](../types/TsgcSTUNResponseErrorEvent.md) | `__property TsgcSTUNResponseErrorEvent OnSTUNResponseError;` |
| `OnSTUNResponseSuccess: TsgcSTUNResponseSuccessEvent` | [TsgcSTUNResponseSuccessEvent](../types/TsgcSTUNResponseSuccessEvent.md) | `__property TsgcSTUNResponseSuccessEvent OnSTUNResponseSuccess;` |
| `OnSTUNBeforeSend: TsgcSTUNBeforeSendEvent` | [TsgcSTUNBeforeSendEvent](../types/TsgcSTUNBeforeSendEvent.md) | `__property TsgcSTUNBeforeSendEvent OnSTUNBeforeSend;` |
| `OnSTUNUnknownMessage: TsgcSTUNUnknownMessageEvent` | [TsgcSTUNUnknownMessageEvent](../types/TsgcSTUNUnknownMessageEvent.md) | `__property TsgcSTUNUnknownMessageEvent OnSTUNUnknownMessage;` |
| `OnDTLSRead: TsgcSTUNDTLSReadEvent` | [TsgcSTUNDTLSReadEvent](../types/TsgcSTUNDTLSReadEvent.md) | `__property TsgcSTUNDTLSReadEvent OnDTLSRead;` |

## Methods

Delphi

```pascal
procedure Clear;
function SendRequest: Boolean;
procedure WriteData(const aBytes: TBytes);
```

C++Builder

```cpp
void __fastcall Clear();
bool __fastcall SendRequest();
void __fastcall WriteData(const System::DynamicArray<System::Byte> aBytes);
```

