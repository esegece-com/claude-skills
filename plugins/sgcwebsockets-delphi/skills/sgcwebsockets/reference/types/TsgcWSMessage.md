# TsgcWSMessage

kind: class
unit: sgcWebSocket_Protocol_sgc_Message

## Properties

| Delphi | Type |
| --- | --- |
| `Text: String` | `String` |
| `Channel: String` | `String` |
| `Guid: String` | `String` |
| `QoS: String` | `String` |
| `Queue: String` | `String` |
| `errorcode: Integer` | `Integer` |
| `errordata: string` | `string` |
| `errormessage: string` | `string` |
| `Id: string` | `string` |
| `JSONResult: IsgcJSON` | [IsgcJSON](./IsgcJSON.md) |
| `method: string` | `string` |
| `params: string` | `string` |
| `result: string` | `string` |
| `version: String (read-only)` | `String` |
| `ThreadId: Cardinal` | `Cardinal` |
| `ConnectionId: String` | `String` |
| `EncodeBase64: Boolean` | `Boolean` |

## Methods

```pascal
procedure Clear(aForceClear: Boolean = False);
procedure Read(const aMessage: String);
function Write: string;
procedure DoEnterRead(const aText: String);
procedure DoLeaveRead;
procedure DoEnterWrite(aForceClear: Boolean = False);
procedure DoLeaveWrite;
```

