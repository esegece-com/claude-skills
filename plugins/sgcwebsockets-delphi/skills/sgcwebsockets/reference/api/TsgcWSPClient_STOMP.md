# TsgcWSPClient_STOMP

unit: sgcWebSocket_Protocols

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Broker: TsgcWSProtocol_Broker_Client` | [TsgcWSProtocol_Broker_Client](../types/TsgcWSProtocol_Broker_Client.md) | `__property TsgcWSProtocol_Broker_Client * Broker;` |
| `Authentication: TsgcWSSTOMPAuthentication_Options` | [TsgcWSSTOMPAuthentication_Options](../types/TsgcWSSTOMPAuthentication_Options.md) | `__property TsgcWSSTOMPAuthentication_Options * Authentication;` |
| `HeartBeat: TsgcWSSTOMPHeartBeat_Options` | [TsgcWSSTOMPHeartBeat_Options](../types/TsgcWSSTOMPHeartBeat_Options.md) | `__property TsgcWSSTOMPHeartBeat_Options * HeartBeat;` |
| `Versions: TsgcWSSTOMPVersion_Options` | [TsgcWSSTOMPVersion_Options](../types/TsgcWSSTOMPVersion_Options.md) | `__property TsgcWSSTOMPVersion_Options * Versions;` |
| `Options: TsgcWSSTOMP_Options` | [TsgcWSSTOMP_Options](../types/TsgcWSSTOMP_Options.md) | `__property TsgcWSSTOMP_Options * Options;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `ConnectHeaders: TStringList` | `TStringList` | `__property TStringList * ConnectHeaders;` |
| `Protocol: string (read-only)` | `string` | `__property UnicodeString Protocol /* read-only */;` |
| `MsgType: TwsProtocolMessage` | [TwsProtocolMessage](../types/TwsProtocolMessage.md) | `__property TwsProtocolMessage * MsgType;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnSTOMPConnected: TsgcWSSTOMPConnectedEvent` | [TsgcWSSTOMPConnectedEvent](../types/TsgcWSSTOMPConnectedEvent.md) | `__property TsgcWSSTOMPConnectedEvent OnSTOMPConnected;` |
| `OnSTOMPMessage: TsgcWSSTOMPMessageEvent` | [TsgcWSSTOMPMessageEvent](../types/TsgcWSSTOMPMessageEvent.md) | `__property TsgcWSSTOMPMessageEvent OnSTOMPMessage;` |
| `OnSTOMPReceipt: TsgcWSSTOMPReceiptEvent` | [TsgcWSSTOMPReceiptEvent](../types/TsgcWSSTOMPReceiptEvent.md) | `__property TsgcWSSTOMPReceiptEvent OnSTOMPReceipt;` |
| `OnSTOMPError: TsgcWSSTOMPErrorEvent` | [TsgcWSSTOMPErrorEvent](../types/TsgcWSSTOMPErrorEvent.md) | `__property TsgcWSSTOMPErrorEvent OnSTOMPError;` |
| `OnSTOMPDisconnected: TsgcWSSTOMPDisconnectedEvent` | [TsgcWSSTOMPDisconnectedEvent](../types/TsgcWSSTOMPDisconnectedEvent.md) | `__property TsgcWSSTOMPDisconnectedEvent OnSTOMPDisconnected;` |
| `OnSTOMPPing: TsgcWSSTOMPPingEvent` | [TsgcWSSTOMPPingEvent](../types/TsgcWSSTOMPPingEvent.md) | `__property TsgcWSSTOMPPingEvent OnSTOMPPing;` |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure Send(const aDestination, aText: string; const aContentType: String = ''; const aTransaction: String = ''; const aCustomHeaders: TStrings = nil);
procedure Subscribe(const aId, aDestination: string; const aACK: TsgcSTOMPACK = ackAuto; const aCustomHeaders: TStrings = nil);
procedure UnSubscribe(const aId: string; const aCustomHeaders: TStrings = nil);
procedure ACK(const aId: string; const aTransaction: String = '');
procedure NACK(const aId: string; const aTransaction: String = '');
procedure BeginTransaction(const aTransaction: String);
procedure CommitTransaction(const aTransaction: String);
procedure AbortTransaction(const aTransaction: String);
procedure Disconnect(const aGraceful: Boolean = True);
procedure Ping;
procedure WriteData(const aText: String);
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Send(const UnicodeString aDestination, const UnicodeString aText, const UnicodeString aContentType = '', const UnicodeString aTransaction = '', const TStrings * aCustomHeaders = nil);
void __fastcall Subscribe(const UnicodeString aId, const UnicodeString aDestination, const TsgcSTOMPACK * aACK = ackAuto, const TStrings * aCustomHeaders = nil);
void __fastcall UnSubscribe(const UnicodeString aId, const TStrings * aCustomHeaders = nil);
void __fastcall ACK(const UnicodeString aId, const UnicodeString aTransaction = '');
void __fastcall NACK(const UnicodeString aId, const UnicodeString aTransaction = '');
void __fastcall BeginTransaction(const UnicodeString aTransaction);
void __fastcall CommitTransaction(const UnicodeString aTransaction);
void __fastcall AbortTransaction(const UnicodeString aTransaction);
void __fastcall Disconnect(const bool aGraceful = True);
void __fastcall Ping();
void __fastcall WriteData(const UnicodeString aText);
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

