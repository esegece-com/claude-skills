# TsgcWSMQTTMessage

kind: class
unit: sgcWebSocket_Protocol_MQTT_Message

## Properties

| Delphi | Type |
| --- | --- |
| `StreamRead: TStream` | `TStream` |
| `ConnectionId: string` | `string` |
| `ThreadId: Cardinal` | `Cardinal` |
| `FixedHeader: TsgcWSMQTTFixedHeader` | [TsgcWSMQTTFixedHeader](./TsgcWSMQTTFixedHeader.md) |
| `VariableHeader: TsgcWSMQTTVariableHeader` | [TsgcWSMQTTVariableHeader](./TsgcWSMQTTVariableHeader.md) |
| `PayLoadHeader: TsgcWSMQTTPayLoadHeader` | [TsgcWSMQTTPayLoadHeader](./TsgcWSMQTTPayLoadHeader.md) |
| `CONNACK: TsgcWSMQTTCONNACK` | [TsgcWSMQTTCONNACK](./TsgcWSMQTTCONNACK.md) |
| `PUBLISH: TsgcWSMQTTPUBLISH` | [TsgcWSMQTTPUBLISH](./TsgcWSMQTTPUBLISH.md) |
| `PUBACK: TsgcWSMQTTPUBACK` | [TsgcWSMQTTPUBACK](./TsgcWSMQTTPUBACK.md) |
| `PUBREC: TsgcWSMQTTPUBREC` | [TsgcWSMQTTPUBREC](./TsgcWSMQTTPUBREC.md) |
| `PUBREL: TsgcWSMQTTPUBREL` | [TsgcWSMQTTPUBREL](./TsgcWSMQTTPUBREL.md) |
| `PUBCOMP: TsgcWSMQTTPUBCOMP` | [TsgcWSMQTTPUBCOMP](./TsgcWSMQTTPUBCOMP.md) |
| `SUBACK: TsgcWSMQTTSUBACK` | [TsgcWSMQTTSUBACK](./TsgcWSMQTTSUBACK.md) |
| `UNSUBACK: TsgcWSMQTTUNSUBACK` | [TsgcWSMQTTUNSUBACK](./TsgcWSMQTTUNSUBACK.md) |
| `DISCONNECT: TsgcWSMQTTDISCONNECT` | [TsgcWSMQTTDISCONNECT](./TsgcWSMQTTDISCONNECT.md) |
| `AUTH: TsgcWSMQTTAUTH` | [TsgcWSMQTTAUTH](./TsgcWSMQTTAUTH.md) |
| `CleanSession: Boolean` | `Boolean` |
| `ClientId: String` | `String` |
| `MQTTVersion: TwsMQTTVersion` | [TwsMQTTVersion](./TwsMQTTVersion.md) |
| `ConnectProperties: TsgcWSMQTTConnect_Properties` | [TsgcWSMQTTConnect_Properties](./TsgcWSMQTTConnect_Properties.md) |
| `WillProperties: TsgcWSMQTTWill_Properties` | [TsgcWSMQTTWill_Properties](./TsgcWSMQTTWill_Properties.md) |
| `PUBLISHProperties: TsgcWSMQTTPublish_Properties` | [TsgcWSMQTTPublish_Properties](./TsgcWSMQTTPublish_Properties.md) |
| `SubscribeProperties: TsgcWSMQTTSubscribe_Properties` | [TsgcWSMQTTSubscribe_Properties](./TsgcWSMQTTSubscribe_Properties.md) |
| `UnsubscribeProperties: TsgcWSMQTTUnsubscribe_Properties` | [TsgcWSMQTTUnsubscribe_Properties](./TsgcWSMQTTUnsubscribe_Properties.md) |
| `DISCONNECTProperties: TsgcWSMQTTDisconnect_Properties` | [TsgcWSMQTTDisconnect_Properties](./TsgcWSMQTTDisconnect_Properties.md) |
| `AUTHProperties: TsgcWSMQTTAuth_Properties` | [TsgcWSMQTTAuth_Properties](./TsgcWSMQTTAuth_Properties.md) |

## Methods

```pascal
function Clone: TsgcWSMQTTMessage;
procedure Clear;
procedure ClearStreamReadTCP;
function Read(const aStream: TStream): Boolean;
function ReadTCP(const aStream: TStream): Boolean;
function DoConnect(aAuthentication: Boolean; aAuthUser, aAuthPass: String; aWillFlag: Boolean; aWillTopic, aWillText: String; aWillQoS: TmqttQoS; aWillRetain, aKeepAliveEnabled: Boolean; aKeepAliveInterval: Integer) : TBytes;
function DoPing: TBytes;
function DoPublish(aPacketIdentifier: Word; const aTopic, aText: String; aQoS: TmqttQoS; aRetain, aDuplicate: Boolean): TBytes;
function DoSubscribe(aPacketIdentifier: Word; aTopics: TsgcWSTopics) : TBytes;
function DoUnSubscribe(aPacketIdentifier: Word; aTopics: TsgcWSTopics) : TBytes;
function DoPubAck(aPacketIdentifier: Word): TBytes;
function DoPubRec(aPacketIdentifier: Word): TBytes;
function DoPubRel(aPacketIdentifier: Word): TBytes;
function DoPubComp(aPacketIdentifier: Word): TBytes;
function DoDisconnect(aReasonCode: Integer = 0): TBytes;
function DoAuth(aReAuthenticate: Boolean): TBytes;
```

