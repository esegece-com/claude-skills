# TsgcWSConnection

kind: class
unit: sgcWebSocket_Classes

## Properties

| Delphi | Type |
| --- | --- |
| `Extensions: TsgcWSExtensions` | [TsgcWSExtensions](./TsgcWSExtensions.md) |
| `QueueOptions: TsgcWSQueueOptions` | [TsgcWSQueueOptions](./TsgcWSQueueOptions.md) |
| `CloseCode: Integer` | `Integer` |
| `MsgError: String` | `String` |
| `Specification: TwsSpecification` | [TwsSpecification](./TwsSpecification.md) |
| `CloseReason: String` | `String` |
| `Masked: Boolean` | `Boolean` |
| `Protocol: String` | `String` |
| `URL: String (read-only)` | `String` |
| `ValidateUTF8: Boolean` | `Boolean` |
| `RaiseDisconnectExceptions: Boolean` | `Boolean` |
| `FragmentedMessages: TwsFragmentedMessages` | [TwsFragmentedMessages](./TwsFragmentedMessages.md) |
| `CleanDisconnect: Boolean` | `Boolean` |
| `Subscriptions: TStringList` | `TStringList` |
| `LastSubscription: String` | `String` |
| `LastUnSubscription: String` | `String` |
| `Disconnected: Boolean` | `Boolean` |
| `LastPing: TDateTime` | `TDateTime` |
| `FirstPing: TDateTime` | `TDateTime` |
| `LastPong: TDateTime` | `TDateTime` |
| `HeadersResponse: TStringList (read-only)` | `TStringList` |
| `Enabled: Boolean (read-only)` | `Boolean` |
| `MsgReceived: String` | `String` |
| `MsgBinaryReceived: TMemoryStream` | `TMemoryStream` |
| `MsgException: String` | `String` |
| `TCPEndOfFrameScanBuffer: TtcpEOFScanBuffer` | [TtcpEOFScanBuffer](./TtcpEOFScanBuffer.md) |
| `Active: Boolean (read-only)` | `Boolean` |
| `Guid: String (read-only)` | `String` |
| `IP: String (read-only)` | `String` |
| `LocalIP: String (read-only)` | `String` |
| `LocalPort: Integer (read-only)` | `Integer` |
| `Port: Integer (read-only)` | `Integer` |
| `IPVersion: TwsIPVersion (read-only)` | [TwsIPVersion](./TwsIPVersion.md) |
| `RecBytes: Int64` | `Int64` |
| `SendBytes: Int64` | `Int64` |
| `Transport: TwsTransport` | [TwsTransport](./TwsTransport.md) |
| `CanFree: Boolean (read-only)` | `Boolean` |
| `LastMsgRcv: TDateTime` | `TDateTime` |
| `CreatedAt: TDateTime` | `TDateTime` |
| `RawException: Exception` | `Exception` |
| `Data: TObject` | `TObject` |

## Events

| Delphi | Type |
| --- | --- |
| `OnUpdate: TsgcWSUpdateEvent` | [TsgcWSUpdateEvent](./TsgcWSUpdateEvent.md) |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](./TsgcWSMessageEvent.md) |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](./TsgcWSBinaryEvent.md) |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](./TsgcWSFragmentedEvent.md) |
| `OnSubscription: TsgcWSSubscriptionEvent` | [TsgcWSSubscriptionEvent](./TsgcWSSubscriptionEvent.md) |
| `OnUnSubscription: TsgcWSSubscriptionEvent` | [TsgcWSSubscriptionEvent](./TsgcWSSubscriptionEvent.md) |
| `OnHandshake: TsgcWSHandshakeEvent` | [TsgcWSHandshakeEvent](./TsgcWSHandshakeEvent.md) |

## Methods

```pascal
procedure DoSubscribe(const aChannels: String);
procedure DoUnSubscribe(const aChannels: String);
function Subscribed(const aChannel: String): Boolean;
procedure Disconnect;
procedure Close;
procedure Ping(const aText: string);
procedure WriteData(const aText: string; const aSize: Integer = 0; const aStreaming: TwsStreaming = stmNone);
function WriteAndWaitData(const aText: String; const aTimeOut: Integer = 10000): string;
procedure AddTCPEndOfFrame(aByte: Byte);
procedure ClearTCPEndOfFrame;
procedure Free;
```

