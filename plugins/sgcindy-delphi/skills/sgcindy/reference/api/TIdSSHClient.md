# TIdSSHClient

unit: IdSSHClient

Add `IdSSHClient` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Host: string` | `string` | `__property UnicodeString Host;` |
| `Port: Word` | `Word` | `__property unsigned short Port;` |
| `Authentication: TIdSSHAuthentication` | [TIdSSHAuthentication](../types/TIdSSHAuthentication.md) | `__property TIdSSHAuthentication * Authentication;` |
| `Algorithms: TIdSSHAlgorithms` | [TIdSSHAlgorithms](../types/TIdSSHAlgorithms.md) | `__property TIdSSHAlgorithms * Algorithms;` |
| `KeepAlive: TIdSSHKeepAlive` | [TIdSSHKeepAlive](../types/TIdSSHKeepAlive.md) | `__property TIdSSHKeepAlive * KeepAlive;` |
| `SSHOptions: TIdSSHOptions` | [TIdSSHOptions](../types/TIdSSHOptions.md) | `__property TIdSSHOptions * SSHOptions;` |
| `DeferReadThread: Boolean` | `Boolean` | `__property bool DeferReadThread;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnSSHConnect: TIdSSHConnectEvent` | [TIdSSHConnectEvent](../types/TIdSSHConnectEvent.md) | `__property TIdSSHConnectEvent OnSSHConnect;` |
| `OnSSHDisconnect: TIdSSHDisconnectEvent` | [TIdSSHDisconnectEvent](../types/TIdSSHDisconnectEvent.md) | `__property TIdSSHDisconnectEvent OnSSHDisconnect;` |
| `OnSSHError: TIdSSHErrorEvent` | [TIdSSHErrorEvent](../types/TIdSSHErrorEvent.md) | `__property TIdSSHErrorEvent OnSSHError;` |
| `OnSSHAuthentication: TIdSSHAuthenticationEvent` | [TIdSSHAuthenticationEvent](../types/TIdSSHAuthenticationEvent.md) | `__property TIdSSHAuthenticationEvent OnSSHAuthentication;` |
| `OnSSHAuthSuccess: TIdSSHAuthSuccessEvent` | [TIdSSHAuthSuccessEvent](../types/TIdSSHAuthSuccessEvent.md) | `__property TIdSSHAuthSuccessEvent OnSSHAuthSuccess;` |
| `OnSSHAuthFailure: TIdSSHAuthFailureEvent` | [TIdSSHAuthFailureEvent](../types/TIdSSHAuthFailureEvent.md) | `__property TIdSSHAuthFailureEvent OnSSHAuthFailure;` |
| `OnSSHAuthBanner: TIdSSHAuthBannerEvent` | [TIdSSHAuthBannerEvent](../types/TIdSSHAuthBannerEvent.md) | `__property TIdSSHAuthBannerEvent OnSSHAuthBanner;` |
| `OnSSHKeyboardInteractive: TIdSSHKeyboardInteractiveEvent` | [TIdSSHKeyboardInteractiveEvent](../types/TIdSSHKeyboardInteractiveEvent.md) | `__property TIdSSHKeyboardInteractiveEvent OnSSHKeyboardInteractive;` |
| `OnSSHHostKey: TIdSSHHostKeyEvent` | [TIdSSHHostKeyEvent](../types/TIdSSHHostKeyEvent.md) | `__property TIdSSHHostKeyEvent OnSSHHostKey;` |
| `OnSSHChannelOpen: TIdSSHChannelOpenEvent` | [TIdSSHChannelOpenEvent](../types/TIdSSHChannelOpenEvent.md) | `__property TIdSSHChannelOpenEvent OnSSHChannelOpen;` |
| `OnSSHChannelClose: TIdSSHChannelCloseEvent` | [TIdSSHChannelCloseEvent](../types/TIdSSHChannelCloseEvent.md) | `__property TIdSSHChannelCloseEvent OnSSHChannelClose;` |
| `OnSSHChannelData: TIdSSHChannelDataEvent` | [TIdSSHChannelDataEvent](../types/TIdSSHChannelDataEvent.md) | `__property TIdSSHChannelDataEvent OnSSHChannelData;` |
| `OnSSHChannelExtendedData: TIdSSHChannelExtendedDataEvent` | [TIdSSHChannelExtendedDataEvent](../types/TIdSSHChannelExtendedDataEvent.md) | `__property TIdSSHChannelExtendedDataEvent OnSSHChannelExtendedData;` |
| `OnSSHChannelEOF: TIdSSHChannelEOFEvent` | [TIdSSHChannelEOFEvent](../types/TIdSSHChannelEOFEvent.md) | `__property TIdSSHChannelEOFEvent OnSSHChannelEOF;` |
| `OnSSHChannelRequest: TIdSSHChannelRequestEvent` | [TIdSSHChannelRequestEvent](../types/TIdSSHChannelRequestEvent.md) | `__property TIdSSHChannelRequestEvent OnSSHChannelRequest;` |
| `OnSSHChannelSuccess: TIdSSHChannelSuccessEvent` | [TIdSSHChannelSuccessEvent](../types/TIdSSHChannelSuccessEvent.md) | `__property TIdSSHChannelSuccessEvent OnSSHChannelSuccess;` |
| `OnSSHChannelFailure: TIdSSHChannelFailureEvent` | [TIdSSHChannelFailureEvent](../types/TIdSSHChannelFailureEvent.md) | `__property TIdSSHChannelFailureEvent OnSSHChannelFailure;` |
| `OnSSHChannelExitStatus: TIdSSHChannelExitStatusEvent` | [TIdSSHChannelExitStatusEvent](../types/TIdSSHChannelExitStatusEvent.md) | `__property TIdSSHChannelExitStatusEvent OnSSHChannelExitStatus;` |
| `OnSSHChannelExitSignal: TIdSSHChannelExitSignalEvent` | [TIdSSHChannelExitSignalEvent](../types/TIdSSHChannelExitSignalEvent.md) | `__property TIdSSHChannelExitSignalEvent OnSSHChannelExitSignal;` |

## Methods

Delphi

```pascal
procedure Connect;
procedure Disconnect;
function Active: Boolean;
function OpenChannel(const aChannelType: string = 'session'): Cardinal;
procedure CloseChannel(aChannelId: Cardinal);
procedure SendChannelData(aChannelId: Cardinal; const aData: TIdBytes);
procedure RequestPTY(aChannelId: Cardinal; const aTerminal: string = 'xterm'; aColumns: Cardinal = 80; aRows: Cardinal = 24; aPixelWidth: Cardinal = 0; aPixelHeight: Cardinal = 0);
procedure RequestShell(aChannelId: Cardinal);
procedure RequestExec(aChannelId: Cardinal; const aCommand: string);
procedure RequestSubsystem(aChannelId: Cardinal; const aSubsystem: string);
procedure SetEnvironmentVariable(aChannelId: Cardinal; const aName, aValue: string);
procedure SendWindowChange(aChannelId: Cardinal; aColumns, aRows, aPixelWidth, aPixelHeight: Cardinal);
procedure SendSignal(aChannelId: Cardinal; const aSignal: string);
procedure SendEOF(aChannelId: Cardinal);
function Execute(const aCommand: string; aTimeout: Integer = 30000): string;
function OpenDirectTCPIP(const aHost: string; aPort: Word; const aOriginatorIP: string = '127.0.0.1'; aOriginatorPort: Word = 0) : Cardinal;
procedure RequestForwarding(const aBindAddress: string; aBindPort: Word);
procedure CancelForwarding(const aBindAddress: string; aBindPort: Word);
procedure Rekey;
procedure StartReadThread;
```

C++Builder

```cpp
void __fastcall Connect();
void __fastcall Disconnect();
bool __fastcall Active();
unsigned int __fastcall OpenChannel(const UnicodeString aChannelType = 'session');
void __fastcall CloseChannel(unsigned int aChannelId);
void __fastcall SendChannelData(unsigned int aChannelId, const TIdBytes * aData);
void __fastcall RequestPTY(unsigned int aChannelId, const UnicodeString aTerminal = 'xterm', unsigned int aColumns = 80, unsigned int aRows = 24, unsigned int aPixelWidth = 0, unsigned int aPixelHeight = 0);
void __fastcall RequestShell(unsigned int aChannelId);
void __fastcall RequestExec(unsigned int aChannelId, const UnicodeString aCommand);
void __fastcall RequestSubsystem(unsigned int aChannelId, const UnicodeString aSubsystem);
void __fastcall SetEnvironmentVariable(unsigned int aChannelId, const UnicodeString aName, const UnicodeString aValue);
void __fastcall SendWindowChange(unsigned int aChannelId, unsigned int aColumns, unsigned int aRows, unsigned int aPixelWidth, unsigned int aPixelHeight);
void __fastcall SendSignal(unsigned int aChannelId, const UnicodeString aSignal);
void __fastcall SendEOF(unsigned int aChannelId);
UnicodeString __fastcall Execute(const UnicodeString aCommand, int aTimeout = 30000);
unsigned int __fastcall OpenDirectTCPIP(const UnicodeString aHost, unsigned short aPort, const UnicodeString aOriginatorIP = '127.0.0.1', unsigned short aOriginatorPort = 0);
void __fastcall RequestForwarding(const UnicodeString aBindAddress, unsigned short aBindPort);
void __fastcall CancelForwarding(const UnicodeString aBindAddress, unsigned short aBindPort);
void __fastcall Rekey();
void __fastcall StartReadThread();
```

