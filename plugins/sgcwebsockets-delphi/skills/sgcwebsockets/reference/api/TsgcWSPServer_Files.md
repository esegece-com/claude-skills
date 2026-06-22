# TsgcWSPServer_Files

unit: sgcWebSocket_Protocols
Edition: Professional and higher

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Server: TsgcWSComponent_Server` | [TsgcWSComponent_Server](../types/TsgcWSComponent_Server.md) | `__property TsgcWSComponent_Server * Server;` |
| `Broker: TsgcWSProtocol_Broker_Server` | [TsgcWSProtocol_Broker_Server](../types/TsgcWSProtocol_Broker_Server.md) | `__property TsgcWSProtocol_Broker_Server * Broker;` |
| `Files: TsgcWSFilesServer_Options` | [TsgcWSFilesServer_Options](../types/TsgcWSFilesServer_Options.md) | `__property TsgcWSFilesServer_Options * Files;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `FileReceivedStreams: TsgcWSFileStreams` | [TsgcWSFileStreams](../types/TsgcWSFileStreams.md) | `__property TsgcWSFileStreams * FileReceivedStreams;` |
| `FileSentStreams: TsgcWSFileStreams` | [TsgcWSFileStreams](../types/TsgcWSFileStreams.md) | `__property TsgcWSFileStreams * FileSentStreams;` |
| `Subscriptions: TsgcQueueListChannels` | [TsgcQueueListChannels](../types/TsgcQueueListChannels.md) | `__property TsgcQueueListChannels * Subscriptions;` |
| `UseMatchesMask: Boolean` | `Boolean` | `__property bool UseMatchesMask;` |
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
| `OnBeforeSubscription: TsgcWSBeforeSubscriptionEvent` | [TsgcWSBeforeSubscriptionEvent](../types/TsgcWSBeforeSubscriptionEvent.md) | `__property TsgcWSBeforeSubscriptionEvent OnBeforeSubscription;` |
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
function WriteData(aGuid, aMessage: string): Boolean;
procedure SendFile(aGuid, aFileName: string; aSize: Integer; aQoS: TwsQoS; aData: String; aFileId: String = '');
procedure BroadcastFile(aFileName: string; aSize: Integer; aData: string; aChannel: string = ''; Exclude: String = ''; Include: String = ''; aFileId: String = '');
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
bool __fastcall WriteData(UnicodeString aGuid, UnicodeString aMessage);
void __fastcall SendFile(UnicodeString aGuid, UnicodeString aFileName, int aSize, TwsQoS * aQoS, UnicodeString aData, UnicodeString aFileId = '');
void __fastcall BroadcastFile(UnicodeString aFileName, int aSize, UnicodeString aData, UnicodeString aChannel = '', UnicodeString Exclude = '', UnicodeString Include = '', UnicodeString aFileId = '');
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

