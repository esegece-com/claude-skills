# TsgcWSPClient_WAMP2

unit: sgcWebSocket_Protocols
Edition: Standard

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
| `OnWAMPSession: TsgcWSSessionEvent` | [TsgcWSSessionEvent](../types/TsgcWSSessionEvent.md) | `__property TsgcWSSessionEvent OnWAMPSession;` |
| `OnWAMPWelcome: TsgcWSWelcomeEvent` | [TsgcWSWelcomeEvent](../types/TsgcWSWelcomeEvent.md) | `__property TsgcWSWelcomeEvent OnWAMPWelcome;` |
| `OnWAMPAbort: TsgcWSAbortEvent` | [TsgcWSAbortEvent](../types/TsgcWSAbortEvent.md) | `__property TsgcWSAbortEvent OnWAMPAbort;` |
| `OnWAMPChallenge: TsgcWSChallengeEvent` | [TsgcWSChallengeEvent](../types/TsgcWSChallengeEvent.md) | `__property TsgcWSChallengeEvent OnWAMPChallenge;` |
| `OnWAMPGoodBye: TsgcWSGoodByeEvent` | [TsgcWSGoodByeEvent](../types/TsgcWSGoodByeEvent.md) | `__property TsgcWSGoodByeEvent OnWAMPGoodBye;` |
| `OnWAMPSubscribed: TsgcWSSubscribedEvent` | [TsgcWSSubscribedEvent](../types/TsgcWSSubscribedEvent.md) | `__property TsgcWSSubscribedEvent OnWAMPSubscribed;` |
| `OnWAMPUnsubscribed: TsgcWSUnsubscribedEvent` | [TsgcWSUnsubscribedEvent](../types/TsgcWSUnsubscribedEvent.md) | `__property TsgcWSUnsubscribedEvent OnWAMPUnsubscribed;` |
| `OnWAMPPublished: TsgcWSPublishedEvent` | [TsgcWSPublishedEvent](../types/TsgcWSPublishedEvent.md) | `__property TsgcWSPublishedEvent OnWAMPPublished;` |
| `OnWAMPEvent: TsgcWSEventEvent` | [TsgcWSEventEvent](../types/TsgcWSEventEvent.md) | `__property TsgcWSEventEvent OnWAMPEvent;` |
| `OnWAMPRegistered: TsgcWSRegisteredEvent` | [TsgcWSRegisteredEvent](../types/TsgcWSRegisteredEvent.md) | `__property TsgcWSRegisteredEvent OnWAMPRegistered;` |
| `OnWAMPUnRegistered: TsgcWSUnRegisteredEvent` | [TsgcWSUnRegisteredEvent](../types/TsgcWSUnRegisteredEvent.md) | `__property TsgcWSUnRegisteredEvent OnWAMPUnRegistered;` |
| `OnWAMPResult: TsgcWSResultEvent` | [TsgcWSResultEvent](../types/TsgcWSResultEvent.md) | `__property TsgcWSResultEvent OnWAMPResult;` |
| `OnWAMPError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnWAMPError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure Subscribe(const aTopic: String; const aOptions: String = '{}'; const aRequestId: Int64 = 0);
procedure UnSubscribe(const aSubscriptionId: Int64; const aRequestId: Int64 = 0);
procedure Abort(const aDetails: String; const aReason: String);
procedure GoodBye(const aDetails: String; const aReason: String);
procedure Publish(const aTopic: String; const aArguments: String = ''; const aArgumentsKw: String = ''; const aOptions: String = '{}'; const aRequestId: Int64 = 0);
procedure Call(const aProcedure: String; const aArguments: String = ''; const aArgumentsKw: String = ''; const aOptions: String = '{}'; const aRequestId: Int64 = 0);
procedure RegisterCall(const aProcedure: String; const aOptions: String = '{}'; const aRequestId: Int64 = 0);
procedure UnRegisterCall(const aRegistrationId: Int64; const aRequestId: Int64 = 0);
procedure Invocation(const aRegistrationId: Int64; const aDetails: String = ''; const aArguments: String = ''; const aArgumentsKw: String = ''; const aRequestId: Int64 = 0);
procedure InvocationError(const aRequestId: Int64; const aDetails: String = '{}'; const aTopic: String = ''; const aArguments: String = ''; const aArgumentsKw: String = '');
procedure WriteData(const aText: String);
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall Subscribe(const UnicodeString aTopic, const UnicodeString aOptions = '{}', const long long aRequestId = 0);
void __fastcall UnSubscribe(const long long aSubscriptionId, const long long aRequestId = 0);
void __fastcall Abort(const UnicodeString aDetails, const UnicodeString aReason);
void __fastcall GoodBye(const UnicodeString aDetails, const UnicodeString aReason);
void __fastcall Publish(const UnicodeString aTopic, const UnicodeString aArguments = '', const UnicodeString aArgumentsKw = '', const UnicodeString aOptions = '{}', const long long aRequestId = 0);
void __fastcall Call(const UnicodeString aProcedure, const UnicodeString aArguments = '', const UnicodeString aArgumentsKw = '', const UnicodeString aOptions = '{}', const long long aRequestId = 0);
void __fastcall RegisterCall(const UnicodeString aProcedure, const UnicodeString aOptions = '{}', const long long aRequestId = 0);
void __fastcall UnRegisterCall(const long long aRegistrationId, const long long aRequestId = 0);
void __fastcall Invocation(const long long aRegistrationId, const UnicodeString aDetails = '', const UnicodeString aArguments = '', const UnicodeString aArgumentsKw = '', const long long aRequestId = 0);
void __fastcall InvocationError(const long long aRequestId, const UnicodeString aDetails = '{}', const UnicodeString aTopic = '', const UnicodeString aArguments = '', const UnicodeString aArgumentsKw = '');
void __fastcall WriteData(const UnicodeString aText);
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

