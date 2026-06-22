# TsgcWSPClient_Files

unit: sgcWebSocket_Protocols
Edition: Professional

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Broker: TsgcWSProtocol_Broker_Client` | [TsgcWSProtocol_Broker_Client](../types/TsgcWSProtocol_Broker_Client.md) | `__property TsgcWSProtocol_Broker_Client * Broker;` |
| `Files: TsgcWSFilesClient_Options` | [TsgcWSFilesClient_Options](../types/TsgcWSFilesClient_Options.md) | `__property TsgcWSFilesClient_Options * Files;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `WSMessageFile: TsgcWSMessageFile` | [TsgcWSMessageFile](../types/TsgcWSMessageFile.md) | `__property TsgcWSMessageFile * WSMessageFile;` |
| `FileReceivedStreams: TsgcWSFileStreams` | [TsgcWSFileStreams](../types/TsgcWSFileStreams.md) | `__property TsgcWSFileStreams * FileReceivedStreams;` |
| `FileSentStreams: TsgcWSFileStreams` | [TsgcWSFileStreams](../types/TsgcWSFileStreams.md) | `__property TsgcWSFileStreams * FileSentStreams;` |
| `Subscriptions: TStringList` | `TStringList` | `__property TStringList * Subscriptions;` |
| `Protocol: string (read-only)` | `string` | `__property UnicodeString Protocol /* read-only */;` |
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
| `OnSubscription: TsgcWSSubscriptionEvent` | [TsgcWSSubscriptionEvent](../types/TsgcWSSubscriptionEvent.md) | `__property TsgcWSSubscriptionEvent OnSubscription;` |
| `OnUnSubscription: TsgcWSSubscriptionEvent` | [TsgcWSSubscriptionEvent](../types/TsgcWSSubscriptionEvent.md) | `__property TsgcWSSubscriptionEvent OnUnSubscription;` |
| `OnFileReceivedAuthorization: TsgcWSFileAuthorizationEvent` | [TsgcWSFileAuthorizationEvent](../types/TsgcWSFileAuthorizationEvent.md) | `__property TsgcWSFileAuthorizationEvent OnFileReceivedAuthorization;` |
| `OnFileReceived: TsgcWSFileEvent` | [TsgcWSFileEvent](../types/TsgcWSFileEvent.md) | `__property TsgcWSFileEvent OnFileReceived;` |
| `OnFileReceivedError: TsgcWSFileErrorEvent` | [TsgcWSFileErrorEvent](../types/TsgcWSFileErrorEvent.md) | `__property TsgcWSFileErrorEvent OnFileReceivedError;` |
| `OnFileReceivedFragment: TsgcWSFileFragmentEvent` | [TsgcWSFileFragmentEvent](../types/TsgcWSFileFragmentEvent.md) | `__property TsgcWSFileFragmentEvent OnFileReceivedFragment;` |
| `OnFileBeforeSent: TsgcWSFileBeforeEvent` | [TsgcWSFileBeforeEvent](../types/TsgcWSFileBeforeEvent.md) | `__property TsgcWSFileBeforeEvent OnFileBeforeSent;` |
| `OnFileSentFragmentRequest: TsgcWSFileFragmentRequestEvent` | [TsgcWSFileFragmentRequestEvent](../types/TsgcWSFileFragmentRequestEvent.md) | `__property TsgcWSFileFragmentRequestEvent OnFileSentFragmentRequest;` |
| `OnFileSentAcknowledgment: TsgcWSFileEvent` | [TsgcWSFileEvent](../types/TsgcWSFileEvent.md) | `__property TsgcWSFileEvent OnFileSentAcknowledgment;` |
| `OnFileSent: TsgcWSFileEvent` | [TsgcWSFileEvent](../types/TsgcWSFileEvent.md) | `__property TsgcWSFileEvent OnFileSent;` |
| `OnFileSentError: TsgcWSFileErrorEvent` | [TsgcWSFileErrorEvent](../types/TsgcWSFileErrorEvent.md) | `__property TsgcWSFileErrorEvent OnFileSentError;` |

## Methods

Delphi

```pascal
procedure WriteData(const aText: String);
procedure Subscribe(const aChannel: String; const aGuid: String = '');
procedure UnSubscribe(const aChannel: String; const aGuid: String = '');
procedure SendFile(aFileName: String; aSize: Integer; aQoS: TwsQoS; aData: String; aFileId: String = '');
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall WriteData(const UnicodeString aText);
void __fastcall Subscribe(const UnicodeString aChannel, const UnicodeString aGuid = '');
void __fastcall UnSubscribe(const UnicodeString aChannel, const UnicodeString aGuid = '');
void __fastcall SendFile(UnicodeString aFileName, int aSize, TwsQoS * aQoS, UnicodeString aData, UnicodeString aFileId = '');
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

