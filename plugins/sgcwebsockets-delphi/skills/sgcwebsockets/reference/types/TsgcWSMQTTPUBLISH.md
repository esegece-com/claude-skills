# TsgcWSMQTTPUBLISH

kind: class
unit: sgcWebSocket_Protocol_MQTT_Message

## Properties

| Delphi | Type |
| --- | --- |
| `Data: TsgcWSMQTTPublishData` | `TsgcWSMQTTPublishData` |
| `PacketIdentifier: Integer` | `Integer` |
| `PUBLISHProperties: TsgcWSMQTTPublishProperties` | `TsgcWSMQTTPublishProperties` |
| `Text: string` | `string` |
| `Topic: String` | `String` |
| `Bytes: TIdBytes (read-only)` | `TIdBytes` |
| `Size: Integer (read-only)` | `Integer` |

## Methods

```pascal
procedure Clear;
procedure AddByte(aByte: Byte);
procedure AddBytes(aBytes: TIdBytes);
procedure AddInteger(aValue: Integer);
procedure AddWord(aValue: Word);
procedure AddString(const aText: String; aHeader: Boolean = True);
procedure AddBoolean(aValue: Boolean);
procedure AddVarInteger(aValue: Integer);
```

