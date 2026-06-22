# TsgcWSMQTTDISCONNECT

kind: class
unit: sgcWebSocket_Protocol_MQTT_Message

## Properties

| Delphi | Type |
| --- | --- |
| `DISCONNECTProperties: TsgcWSMQTTDISCONNECTProperties` | `TsgcWSMQTTDISCONNECTProperties` |
| `ReasonCode: Integer` | `Integer` |
| `ReasonName: string` | `string` |
| `PacketIdentifier: Integer` | `Integer` |
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

