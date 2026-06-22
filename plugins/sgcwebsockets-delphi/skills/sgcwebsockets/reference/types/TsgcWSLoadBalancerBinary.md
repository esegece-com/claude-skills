# TsgcWSLoadBalancerBinary

kind: class
unit: sgcWebSocket_LoadBalancer_Message

## Properties

| Delphi | Type |
| --- | --- |
| `Channel: string` | `string` |
| `Exclude: string` | `string` |
| `Guid: String` | `String` |
| `Include: string` | `string` |
| `Protocol: String` | `String` |
| `Size: Integer` | `Integer` |
| `Streaming: TwsStreaming` | [TwsStreaming](./TwsStreaming.md) |

## Methods

```pascal
procedure Clear;
procedure Read(var aStream: TMemoryStream);
procedure Write(var aData: TMemoryStream);
```

