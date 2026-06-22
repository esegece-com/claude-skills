# TsgcWSPClient_MQTT

unit: sgcWebSocket_Protocols

Add `sgcWebSocket_Protocols` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Client: TsgcWSComponent_WSClient` | [TsgcWSComponent_WSClient](../types/TsgcWSComponent_WSClient.md) | `__property TsgcWSComponent_WSClient * Client;` |
| `Broker: TsgcWSProtocol_Broker_Client` | [TsgcWSProtocol_Broker_Client](../types/TsgcWSProtocol_Broker_Client.md) | `__property TsgcWSProtocol_Broker_Client * Broker;` |
| `Authentication: TsgcWSMQTTAuthentication_Options` | [TsgcWSMQTTAuthentication_Options](../types/TsgcWSMQTTAuthentication_Options.md) | `__property TsgcWSMQTTAuthentication_Options * Authentication;` |
| `HeartBeat: TsgcWSMQTTHeartBeat_Options` | [TsgcWSMQTTHeartBeat_Options](../types/TsgcWSMQTTHeartBeat_Options.md) | `__property TsgcWSMQTTHeartBeat_Options * HeartBeat;` |
| `LastWillTestament: TsgcWSMQTTLWT_Options` | [TsgcWSMQTTLWT_Options](../types/TsgcWSMQTTLWT_Options.md) | `__property TsgcWSMQTTLWT_Options * LastWillTestament;` |
| `QoS: TsgcWSMQTTQoS_Options` | [TsgcWSMQTTQoS_Options](../types/TsgcWSMQTTQoS_Options.md) | `__property TsgcWSMQTTQoS_Options * QoS;` |
| `ConnectProperties: TsgcWSMQTTConnect_Properties` | [TsgcWSMQTTConnect_Properties](../types/TsgcWSMQTTConnect_Properties.md) | `__property TsgcWSMQTTConnect_Properties * ConnectProperties;` |
| `MQTTVersion: TwsMQTTVersion` | [TwsMQTTVersion](../types/TwsMQTTVersion.md) | `__property TwsMQTTVersion * MQTTVersion;` |
| `Guid: String` | `String` | `__property UnicodeString Guid;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `SndMsg: TsgcWSMQTTMessage (read-only)` | [TsgcWSMQTTMessage](../types/TsgcWSMQTTMessage.md) | `__property TsgcWSMQTTMessage * SndMsg /* read-only */;` |
| `RcvMsg: TsgcWSMQTTMessage (read-only)` | [TsgcWSMQTTMessage](../types/TsgcWSMQTTMessage.md) | `__property TsgcWSMQTTMessage * RcvMsg /* read-only */;` |
| `Protocol: string (read-only)` | `string` | `__property UnicodeString Protocol /* read-only */;` |
| `MsgType: TwsProtocolMessage` | [TwsProtocolMessage](../types/TwsProtocolMessage.md) | `__property TwsProtocolMessage * MsgType;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnMQTTBeforeConnect: TsgcWSMQTTBeforeConnectEvent` | [TsgcWSMQTTBeforeConnectEvent](../types/TsgcWSMQTTBeforeConnectEvent.md) | `__property TsgcWSMQTTBeforeConnectEvent OnMQTTBeforeConnect;` |
| `OnMQTTConnect: TsgcWSMQTTConnectEvent` | [TsgcWSMQTTConnectEvent](../types/TsgcWSMQTTConnectEvent.md) | `__property TsgcWSMQTTConnectEvent OnMQTTConnect;` |
| `OnMQTTPing: TsgcWSMQTTPingEvent` | [TsgcWSMQTTPingEvent](../types/TsgcWSMQTTPingEvent.md) | `__property TsgcWSMQTTPingEvent OnMQTTPing;` |
| `OnMQTTPublish: TsgcWSMQTTPublishEvent` | [TsgcWSMQTTPublishEvent](../types/TsgcWSMQTTPublishEvent.md) | `__property TsgcWSMQTTPublishEvent OnMQTTPublish;` |
| `OnMQTTPublishEx: TsgcWSMQTTPublishExEvent` | [TsgcWSMQTTPublishExEvent](../types/TsgcWSMQTTPublishExEvent.md) | `__property TsgcWSMQTTPublishExEvent OnMQTTPublishEx;` |
| `OnMQTTPubAck: TsgcWSMQTTPubAckEvent` | [TsgcWSMQTTPubAckEvent](../types/TsgcWSMQTTPubAckEvent.md) | `__property TsgcWSMQTTPubAckEvent OnMQTTPubAck;` |
| `OnMQTTPubRec: TsgcWSMQTTPubRecEvent` | [TsgcWSMQTTPubRecEvent](../types/TsgcWSMQTTPubRecEvent.md) | `__property TsgcWSMQTTPubRecEvent OnMQTTPubRec;` |
| `OnMQTTPubRel: TsgcWSMQTTPubRelEvent` | [TsgcWSMQTTPubRelEvent](../types/TsgcWSMQTTPubRelEvent.md) | `__property TsgcWSMQTTPubRelEvent OnMQTTPubRel;` |
| `OnMQTTPubComp: TsgcWSMQTTPubCompEvent` | [TsgcWSMQTTPubCompEvent](../types/TsgcWSMQTTPubCompEvent.md) | `__property TsgcWSMQTTPubCompEvent OnMQTTPubComp;` |
| `OnMQTTSubscribe: TsgcWSMQTTSubscribeEvent` | [TsgcWSMQTTSubscribeEvent](../types/TsgcWSMQTTSubscribeEvent.md) | `__property TsgcWSMQTTSubscribeEvent OnMQTTSubscribe;` |
| `OnMQTTUnSubscribe: TsgcWSMQTTUnSubscribeEvent` | [TsgcWSMQTTUnSubscribeEvent](../types/TsgcWSMQTTUnSubscribeEvent.md) | `__property TsgcWSMQTTUnSubscribeEvent OnMQTTUnSubscribe;` |
| `OnMQTTDisconnect: TsgcWSMQTTDisconnectEvent` | [TsgcWSMQTTDisconnectEvent](../types/TsgcWSMQTTDisconnectEvent.md) | `__property TsgcWSMQTTDisconnectEvent OnMQTTDisconnect;` |
| `OnMQTTAuth: TsgcWSMQTTAuthEvent` | [TsgcWSMQTTAuthEvent](../types/TsgcWSMQTTAuthEvent.md) | `__property TsgcWSMQTTAuthEvent OnMQTTAuth;` |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure WriteData(const aText: String);
procedure Connect;
procedure Ping;
function Publish(const aTopic, aText: String; aQoS: TmqttQoS = mtqsAtMostOnce; aRetain: Boolean = False; const aPublishProperties: TsgcWSMQTTPublish_Properties = nil) : Word;
function PublishAndWait(const aTopic, aText: String; aQoS: TmqttQoS = mtqsAtMostOnce; aRetain: Boolean = False; const aPublishProperties: TsgcWSMQTTPublish_Properties = nil; const aTimeout: Integer = 10000): Boolean;
function Subscribe(const aTopic: String; aQoS: TmqttQoS = mtqsAtMostOnce; const aSubscribeProperties: TsgcWSMQTTSubscribe_Properties = nil) : Word;
function UnSubscribe(const aTopic: string; aUnsubscribeProperties: TsgcWSMQTTUnsubscribe_Properties = nil) : Word;
procedure Disconnect;
procedure Auth(aReAuthenticate: Boolean; aAuthProperties: TsgcWSMQTTAuth_Properties = nil);
procedure EnterCS;
procedure LeaveCS;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall WriteData(const UnicodeString aText);
void __fastcall Connect();
void __fastcall Ping();
unsigned short __fastcall Publish(const UnicodeString aTopic, const UnicodeString aText, TmqttQoS * aQoS = mtqsAtMostOnce, bool aRetain = False, const TsgcWSMQTTPublish_Properties * aPublishProperties = nil);
bool __fastcall PublishAndWait(const UnicodeString aTopic, const UnicodeString aText, TmqttQoS * aQoS = mtqsAtMostOnce, bool aRetain = False, const TsgcWSMQTTPublish_Properties * aPublishProperties = nil, const int aTimeout = 10000);
unsigned short __fastcall Subscribe(const UnicodeString aTopic, TmqttQoS * aQoS = mtqsAtMostOnce, const TsgcWSMQTTSubscribe_Properties * aSubscribeProperties = nil);
unsigned short __fastcall UnSubscribe(const UnicodeString aTopic, TsgcWSMQTTUnsubscribe_Properties * aUnsubscribeProperties = nil);
void __fastcall Disconnect();
void __fastcall Auth(bool aReAuthenticate, TsgcWSMQTTAuth_Properties * aAuthProperties = nil);
void __fastcall EnterCS();
void __fastcall LeaveCS();
void __fastcall QueueClear();
```

