# TsgcUDPCLient

unit: sgcP2P
Edition: Standard

Add `sgcP2P` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Host: String` | `String` | `__property UnicodeString Host;` |
| `Port: Integer` | `Integer` | `__property int Port;` |
| `IPVersion: TIdIPVersion` | `TIdIPVersion` | `__property TIdIPVersion * IPVersion;` |
| `LogFile: TsgcUDPLogFile` | [TsgcUDPLogFile](../types/TsgcUDPLogFile.md) | `__property TsgcUDPLogFile * LogFile;` |
| `Proxy: TsgcUDPProxy_Options` | [TsgcUDPProxy_Options](../types/TsgcUDPProxy_Options.md) | `__property TsgcUDPProxy_Options * Proxy;` |
| `NotifyEvents: TwsNotifyEvent` | [TwsNotifyEvent](../types/TwsNotifyEvent.md) | `__property TwsNotifyEvent NotifyEvents;` |
| `DTLS: Boolean` | `Boolean` | `__property bool DTLS;` |
| `DTLSOptions: TsgcUDPDTLSClient_Options` | [TsgcUDPDTLSClient_Options](../types/TsgcUDPDTLSClient_Options.md) | `__property TsgcUDPDTLSClient_Options * DTLSOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `UseNagle: Boolean` | `Boolean` | `__property bool UseNagle;` |
| `UDPMode: TsgcUDPMode` | [TsgcUDPMode](../types/TsgcUDPMode.md) | `__property TsgcUDPMode * UDPMode;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnUDPRead: TUDPReadEvent` | [TUDPReadEvent](../types/TUDPReadEvent.md) | `__property TUDPReadEvent OnUDPRead;` |
| `OnUDPException: TIdUDPExceptionEvent` | [TIdUDPExceptionEvent](../types/TIdUDPExceptionEvent.md) | `__property TIdUDPExceptionEvent OnUDPException;` |
| `OnDTLSVerifyPeer: TsgcUDPDTLSVerifyPeerEvent` | [TsgcUDPDTLSVerifyPeerEvent](../types/TsgcUDPDTLSVerifyPeerEvent.md) | `__property TsgcUDPDTLSVerifyPeerEvent OnDTLSVerifyPeer;` |

## Methods

Delphi

```pascal
procedure AddCommand(const aCommand: TsgcUDPCommands);
procedure AddBytes(const ABytes: TIdBytes);
procedure ClearDTLS;
procedure WriteData(const aIPAddress: string; aPort: Word; const aValue: string);
procedure EnterCS;
procedure LeaveCS;
```

C++Builder

```cpp
void __fastcall AddCommand(const TsgcUDPCommands * aCommand);
void __fastcall AddBytes(const TIdBytes * ABytes);
void __fastcall ClearDTLS();
void __fastcall WriteData(const UnicodeString aIPAddress, unsigned short aPort, const UnicodeString aValue);
void __fastcall EnterCS();
void __fastcall LeaveCS();
```

