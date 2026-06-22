# TsgcWSMessageFile

kind: class
unit: sgcWebSocket_Protocol_Files_Message

## Properties

| Delphi | Type |
| --- | --- |
| `BufferSize: Integer` | `Integer` |
| `Channel: String` | `String` |
| `Method: String` | `String` |
| `FileId: String` | `String` |
| `Data: string` | `string` |
| `FileName: String` | `String` |
| `FilePosition: Int64` | `Int64` |
| `FileSize: Int64` | `Int64` |
| `Id: string` | `string` |
| `QoS: string` | `string` |
| `Streaming: string` | `string` |
| `Text: String` | `String` |
| `ConnectionId: string` | `string` |
| `ThreadId: cardinal` | `cardinal` |

## Methods

```pascal
procedure Read(const aText: String);
function Write: string;
procedure Clear;
```

