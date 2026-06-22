# TsgcHTTP2ConnectionClient

kind: class
unit: sgcHTTP2_Client

## Properties

| Delphi | Type |
| --- | --- |
| `Response: TsgcHTTP2Response` | [TsgcHTTP2Response](./TsgcHTTP2Response.md) |
| `TLS: Boolean` | `Boolean` |
| `Host: String (read-only)` | `String` |
| `ALPNProtocol: string (read-only)` | `string` |
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
| `Disconnected: Boolean` | `Boolean` |
| `RawException: Exception` | `Exception` |
| `Data: TObject` | `TObject` |

## Events

| Delphi | Type |
| --- | --- |
| `OnCommand: TsgcHTTP2ClientCommandEvent` | [TsgcHTTP2ClientCommandEvent](./TsgcHTTP2ClientCommandEvent.md) |
| `OnConnect: TsgcHTTP2ClientConnectEvent` | [TsgcHTTP2ClientConnectEvent](./TsgcHTTP2ClientConnectEvent.md) |
| `OnGoAway: TsgcHTTP2ClientGoAwayEvent` | [TsgcHTTP2ClientGoAwayEvent](./TsgcHTTP2ClientGoAwayEvent.md) |
| `OnRSTStream: TsgcHTTP2ClientRSTStreamEvent` | [TsgcHTTP2ClientRSTStreamEvent](./TsgcHTTP2ClientRSTStreamEvent.md) |
| `OnStreamResponse: TsgcHTTP2ClientStreamResponseEvent` | [TsgcHTTP2ClientStreamResponseEvent](./TsgcHTTP2ClientStreamResponseEvent.md) |
| `OnStreamResponseFragment: TsgcHTTP2ClientStreamResponseFragmentEvent` | [TsgcHTTP2ClientStreamResponseFragmentEvent](./TsgcHTTP2ClientStreamResponseFragmentEvent.md) |
| `OnPushPromise: TsgcHTTP2ClientPushPromiseEvent` | [TsgcHTTP2ClientPushPromiseEvent](./TsgcHTTP2ClientPushPromiseEvent.md) |
| `OnException: TsgcHTTP2ClientExceptionEvent` | [TsgcHTTP2ClientExceptionEvent](./TsgcHTTP2ClientExceptionEvent.md) |
| `OnBeforeRequest: TsgcHTTPClientBeforeRequestEvent` | [TsgcHTTPClientBeforeRequestEvent](./TsgcHTTPClientBeforeRequestEvent.md) |
| `OnBinary: TsgcTCPBinaryEvent` | [TsgcTCPBinaryEvent](./TsgcTCPBinaryEvent.md) |
| `OnBeforeDisconnect: TNotifyEvent` | `TNotifyEvent` |

## Methods

```pascal
procedure Close(aCode: Th2ErrorCodes = h2erNO_ERROR; const aDescription: String = '');
procedure Disconnect;
procedure Ping;
procedure CancelStream(aStreamIdentifier: Integer; aError: Th2ErrorCodes);
procedure Connect(const aPath: string; aResponseContent: TStream = nil; const aRequest: TsgcHTTP2Request = nil);
procedure Delete(const aPath: string; aResponseContent: TStream = nil; const aRequest: TsgcHTTP2Request = nil);
procedure Options(const aPath: string; aResponseContent: TStream = nil; const aRequest: TsgcHTTP2Request = nil);
procedure Get(const aPath: string; aResponseContent: TStream = nil; const aRequest: TsgcHTTP2Request = nil);
procedure Post(const aPath: string; const aSource: TStream; const aResponseContent: TStream = nil; const aRequest: TsgcHTTP2Request = nil);
procedure Put(const aPath: string; const aSource: TStream; const aResponseContent: TStream = nil; const aRequest: TsgcHTTP2Request = nil);
procedure Patch(const aPath: string; const aSource: TStream; const aResponseContent: TStream = nil; const aRequest: TsgcHTTP2Request = nil);
procedure Trace(const aPath: string; aResponseContent: TStream = nil; const aRequest: TsgcHTTP2Request = nil);
procedure Head(const aPath: string; const aRequest: TsgcHTTP2Request = nil);
procedure DisconnectPeer(aCallOnDisconnectIfClosed : Boolean = False);
procedure AddTCPEndOfFrame(aByte: Byte);
procedure ClearTCPEndOfFrame;
procedure Free;
```

