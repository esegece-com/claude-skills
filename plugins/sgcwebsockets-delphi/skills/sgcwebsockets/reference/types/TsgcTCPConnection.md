# TsgcTCPConnection

kind: class
unit: sgcTCP_Classes

## Properties

| Delphi | Type |
| --- | --- |
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

## Methods

```pascal
procedure AddTCPEndOfFrame(aByte: Byte);
procedure ClearTCPEndOfFrame;
procedure Free;
```

