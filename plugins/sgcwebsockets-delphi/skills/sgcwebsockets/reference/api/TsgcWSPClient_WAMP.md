# TsgcWSPClient_WAMP

unit: sgcWebSocket_Protocols
Edition: Professional and higher

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Broker: TsgcWSProtocol_Broker_Client` | [TsgcWSProtocol_Broker_Client](../types/TsgcWSProtocol_Broker_Client.md) | `__property TsgcWSProtocol_Broker_Client * Broker;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `Protocol: string (read-only)` | `string` | `__property UnicodeString Protocol /* read-only */;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `MsgType: TwsProtocolMessage` | [TwsProtocolMessage](../types/TwsProtocolMessage.md) | `__property TwsProtocolMessage * MsgType;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnRawMessage: TsgcOnWhatsAppServerMessage` | [TsgcOnWhatsAppServerMessage](../types/TsgcOnWhatsAppServerMessage.md) | `__property TsgcOnWhatsAppServerMessage * OnRawMessage;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |
| `OnWelcome: TsgcWSWelcomeEvent` | [TsgcWSWelcomeEvent](../types/TsgcWSWelcomeEvent.md) | `__property TsgcWSWelcomeEvent OnWelcome;` |
| `OnCallResult: TsgcWSCallResultEvent` | [TsgcWSCallResultEvent](../types/TsgcWSCallResultEvent.md) | `__property TsgcWSCallResultEvent OnCallResult;` |
| `OnCallProgressResult: TsgcWSCallProgresslResultEvent` | [TsgcWSCallProgresslResultEvent](../types/TsgcWSCallProgresslResultEvent.md) | `__property TsgcWSCallProgresslResultEvent OnCallProgressResult;` |
| `OnCallError: TsgcWSCallErrorEvent` | [TsgcWSCallErrorEvent](../types/TsgcWSCallErrorEvent.md) | `__property TsgcWSCallErrorEvent OnCallError;` |
| `OnEvent: TsgcWSEvent` | [TsgcWSEvent](../types/TsgcWSEvent.md) | `__property TsgcWSEvent OnEvent;` |

## Methods

Delphi

```pascal
procedure Prefix(const aPrefix, aURI: String);
procedure Subscribe(const aTopicURI: String);
procedure UnSubscribe(const aTopicURI: String);
procedure Call(const aCallId, aProcURI: String; aArguments: String = '');
procedure CancelCall(const aCallId: string);
procedure Publish(const aTopicURI, aEvent: string; const aExclude: string = ''; const aEligible: String = '');
procedure WriteData(const aText: String);
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Prefix(const UnicodeString aPrefix, const UnicodeString aURI);
void __fastcall Subscribe(const UnicodeString aTopicURI);
void __fastcall UnSubscribe(const UnicodeString aTopicURI);
void __fastcall Call(const UnicodeString aCallId, const UnicodeString aProcURI, UnicodeString aArguments = '');
void __fastcall CancelCall(const UnicodeString aCallId);
void __fastcall Publish(const UnicodeString aTopicURI, const UnicodeString aEvent, const UnicodeString aExclude = '', const UnicodeString aEligible = '');
void __fastcall WriteData(const UnicodeString aText);
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

