# TsgcWSExtensions

kind: class
unit: sgcWebSocket_Extensions

## Properties

| Delphi | Type |
| --- | --- |
| `List: TStringList (read-only)` | `TStringList` |
| `ExtensionNegotiated: Boolean (read-only)` | `Boolean` |
| `Compression: Boolean (read-only)` | `Boolean` |
| `Mode: TwsApplicationMode` | [TwsApplicationMode](./TwsApplicationMode.md) |
| `MaxDecompressedSize: Int64` | `Int64` |
| `DeflateFrame: TsgcWSExtension_DeflateFrame` | `TsgcWSExtension_DeflateFrame` |
| `PerMessage_Deflate: TsgcWSExtension_PerMessage_Deflate` | `TsgcWSExtension_PerMessage_Deflate` |

## Methods

```pascal
procedure Assign(aSource: TPersistent);
procedure DecodeHeader(aByte: Byte);
procedure EncodeHeader(var aByte: Byte);
procedure DecodeExtensions(const aExtensions: String);
procedure WriteHeader(aHeader: TStringList);
procedure ReadStream(var aStream: TStream);
procedure WriteStream(var aStream: TStream);
```

