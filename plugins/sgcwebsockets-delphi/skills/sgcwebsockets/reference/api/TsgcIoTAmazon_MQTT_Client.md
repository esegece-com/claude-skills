# TsgcIoTAmazon_MQTT_Client

unit: sgcIoT
Edition: Standard

Add `sgcIoT` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `Certificate: PX509 (read-only)` | `PX509` | `__property PX509 Certificate /* read-only */;` |
| `Amazon: TsgcIoT_Amazon_MQTT_Client_Options` | [TsgcIoT_Amazon_MQTT_Client_Options](../types/TsgcIoT_Amazon_MQTT_Client_Options.md) | `__property TsgcIoT_Amazon_MQTT_Client_Options * Amazon;` |
| `MQTTHeartBeat: TsgcWSMQTTHeartBeat_Options` | [TsgcWSMQTTHeartBeat_Options](../types/TsgcWSMQTTHeartBeat_Options.md) | `__property TsgcWSMQTTHeartBeat_Options * MQTTHeartBeat;` |
| `MQTTAuthentication: TsgcWSMQTTAuthentication_Options` | [TsgcWSMQTTAuthentication_Options](../types/TsgcWSMQTTAuthentication_Options.md) | `__property TsgcWSMQTTAuthentication_Options * MQTTAuthentication;` |
| `WatchDog: TsgcWSWatchDogClient_Options` | [TsgcWSWatchDogClient_Options](../types/TsgcWSWatchDogClient_Options.md) | `__property TsgcWSWatchDogClient_Options * WatchDog;` |
| `LogFile: TsgcAWSLogFile` | [TsgcAWSLogFile](../types/TsgcAWSLogFile.md) | `__property TsgcAWSLogFile * LogFile;` |
| `SignatureV4: TsgcIoT_Amazon_MQTT_Signature_V4_Options` | [TsgcIoT_Amazon_MQTT_Signature_V4_Options](../types/TsgcIoT_Amazon_MQTT_Signature_V4_Options.md) | `__property TsgcIoT_Amazon_MQTT_Signature_V4_Options * SignatureV4;` |
| `CustomAuthentication: TsgcIoT_Amazon_MQTT_Custom_Authentication_Options` | [TsgcIoT_Amazon_MQTT_Custom_Authentication_Options](../types/TsgcIoT_Amazon_MQTT_Custom_Authentication_Options.md) | `__property TsgcIoT_Amazon_MQTT_Custom_Authentication_Options * CustomAuthentication;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `BoundIP: string` | `string` | `__property UnicodeString BoundIP;` |
| `BoundPort: TIdPort` | `TIdPort` | `__property TIdPort * BoundPort;` |
| `BoundPortMax: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMax;` |
| `BoundPortMin: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMin;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcHTTP2ClientConnectEvent` | [TsgcHTTP2ClientConnectEvent](../types/TsgcHTTP2ClientConnectEvent.md) | `__property TsgcHTTP2ClientConnectEvent OnConnect;` |
| `OnDisconnect: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnDisconnect;` |
| `OnException: TsgcAMQP1OnExceptionEvent` | [TsgcAMQP1OnExceptionEvent](../types/TsgcAMQP1OnExceptionEvent.md) | `__property TsgcAMQP1OnExceptionEvent OnException;` |
| `OnError: TsgcHTTP3ErrorEvent` | `TsgcHTTP3ErrorEvent` | `__property TsgcHTTP3ErrorEvent OnError;` |
| `OnMQTTBeforeConnect: TsgcIoTMQTTBeforeConnectEvent` | `TsgcIoTMQTTBeforeConnectEvent` | `__property TsgcIoTMQTTBeforeConnectEvent OnMQTTBeforeConnect;` |
| `OnMQTTConnect: TsgcIoTMQTTConnectEvent` | `TsgcIoTMQTTConnectEvent` | `__property TsgcIoTMQTTConnectEvent OnMQTTConnect;` |
| `OnMQTTPublish: TsgcIoTMQTTPublishEvent` | `TsgcIoTMQTTPublishEvent` | `__property TsgcIoTMQTTPublishEvent OnMQTTPublish;` |
| `OnMQTTPublishEx: TsgcIoTMQTTPublishExEvent` | `TsgcIoTMQTTPublishExEvent` | `__property TsgcIoTMQTTPublishExEvent OnMQTTPublishEx;` |
| `OnMQTTPubAck: TsgcIoTMQTTPubAckEvent` | `TsgcIoTMQTTPubAckEvent` | `__property TsgcIoTMQTTPubAckEvent OnMQTTPubAck;` |
| `OnMQTTSubscribe: TsgcIoTMQTTSubscribeEvent` | `TsgcIoTMQTTSubscribeEvent` | `__property TsgcIoTMQTTSubscribeEvent OnMQTTSubscribe;` |
| `OnMQTTUnSubscribe: TsgcIoTMQTTUnSubscribeEvent` | `TsgcIoTMQTTUnSubscribeEvent` | `__property TsgcIoTMQTTUnSubscribeEvent OnMQTTUnSubscribe;` |
| `OnMQTTDisconnect: TsgcIoTMQTTDisconnectEvent` | `TsgcIoTMQTTDisconnectEvent` | `__property TsgcIoTMQTTDisconnectEvent OnMQTTDisconnect;` |
| `OnMQTTPing: TsgcIoTMQTTPingEvent` | `TsgcIoTMQTTPingEvent` | `__property TsgcIoTMQTTPingEvent OnMQTTPing;` |
| `OnMQTTPubRec: TsgcIoTMQTTPubRecEvent` | `TsgcIoTMQTTPubRecEvent` | `__property TsgcIoTMQTTPubRecEvent OnMQTTPubRec;` |
| `OnMQTTPubComp: TsgcIoTMQTTPubCompEvent` | `TsgcIoTMQTTPubCompEvent` | `__property TsgcIoTMQTTPubCompEvent OnMQTTPubComp;` |

## Methods

Delphi

```pascal
procedure Subscribe_ClientConnected(const aClientId: String);
procedure Subscribe_ClientDisconnected(const aClientId: String);
procedure Subscribe_ClientSubscribed(const aClientId: String);
procedure Subscribe_ClientUnSubscribed(const aClientId: String);
procedure Publish_Rule(const aRuleName, aText: String);
procedure Publish_DeleteShadow(const aThingName, aText: String);
procedure Subscribe_DeleteShadow(const aThingName: String);
procedure Subscribe_ShadowDeleted(const aThingName: String);
procedure Subscribe_ShadowRejected(const aThingName: String);
procedure Publish_ShadowGet(const aThingName, aText: String);
procedure Subscribe_ShadowGet(const aThingName: String);
procedure Subscribe_ShadowGetAccepted(const aThingName: String);
procedure Subscribe_ShadowGetRejected(const aThingName: String);
procedure Publish_ShadowUpdate(const aThingName, aText: String);
procedure Subscribe_ShadowUpdateAccepted(const aThingName: String);
procedure Subscribe_ShadowUpdateRejected(const aThingName: String);
procedure Subscribe_ShadowUpdateDelta(const aThingName: String);
procedure Subscribe_ShadowUpdateDocuments(const aThingName: String);
procedure CreateCertificateFromCsr(const aCertificateSigningRequest: string; const aPayloadFormat: string = 'json');
procedure SubscribeCreateCertificateFromCsrResponse(const aPayloadFormat : string = 'json');
procedure SubscribeCreateCertificateFromCsrError(const aPayloadFormat : string = 'json');
procedure CreateKeysAndCertificate(const aPayloadFormat: string = 'json');
procedure SubscribeCreateKeysAndCertificateResponse(const aPayloadFormat : string = 'json');
procedure SubscribeCreateKeysAndCertificateError(const aPayloadFormat : string = 'json');
procedure RegisterThing(const aTemplateName, aPayload: string; const aPayloadFormat: string = 'json');
procedure SubscribeRegisterThingResponse(const aTemplateName: string; const aPayloadFormat: string = 'json');
procedure SubscribeRegisterThingError(const aTemplateName: string; const aPayloadFormat: string = 'json');
procedure Subscribe(const aTopic: String; aQoS: TawsIoTQoS = awsIoTQoS0);
procedure Publish(const aTopic, aText: String; aQoS: TawsIoTQoS = awsIoTQoS0);
procedure UnSubscribe(const aTopic: String);
function PublishAndWait(const aTopic, aText: String; aQoS: TmqttQoS = mtqsAtMostOnce; aRetain: Boolean = False; const aTimeout: integer = 10000): Boolean;
function Disconnect(aTimeout: Integer = 10000): Boolean;
```

C++Builder

```cpp
void __fastcall Subscribe_ClientConnected(const UnicodeString aClientId);
void __fastcall Subscribe_ClientDisconnected(const UnicodeString aClientId);
void __fastcall Subscribe_ClientSubscribed(const UnicodeString aClientId);
void __fastcall Subscribe_ClientUnSubscribed(const UnicodeString aClientId);
void __fastcall Publish_Rule(const UnicodeString aRuleName, const UnicodeString aText);
void __fastcall Publish_DeleteShadow(const UnicodeString aThingName, const UnicodeString aText);
void __fastcall Subscribe_DeleteShadow(const UnicodeString aThingName);
void __fastcall Subscribe_ShadowDeleted(const UnicodeString aThingName);
void __fastcall Subscribe_ShadowRejected(const UnicodeString aThingName);
void __fastcall Publish_ShadowGet(const UnicodeString aThingName, const UnicodeString aText);
void __fastcall Subscribe_ShadowGet(const UnicodeString aThingName);
void __fastcall Subscribe_ShadowGetAccepted(const UnicodeString aThingName);
void __fastcall Subscribe_ShadowGetRejected(const UnicodeString aThingName);
void __fastcall Publish_ShadowUpdate(const UnicodeString aThingName, const UnicodeString aText);
void __fastcall Subscribe_ShadowUpdateAccepted(const UnicodeString aThingName);
void __fastcall Subscribe_ShadowUpdateRejected(const UnicodeString aThingName);
void __fastcall Subscribe_ShadowUpdateDelta(const UnicodeString aThingName);
void __fastcall Subscribe_ShadowUpdateDocuments(const UnicodeString aThingName);
void __fastcall CreateCertificateFromCsr(const UnicodeString aCertificateSigningRequest, const UnicodeString aPayloadFormat = 'json');
void __fastcall SubscribeCreateCertificateFromCsrResponse(const UnicodeString aPayloadFormat = 'json');
void __fastcall SubscribeCreateCertificateFromCsrError(const UnicodeString aPayloadFormat = 'json');
void __fastcall CreateKeysAndCertificate(const UnicodeString aPayloadFormat = 'json');
void __fastcall SubscribeCreateKeysAndCertificateResponse(const UnicodeString aPayloadFormat = 'json');
void __fastcall SubscribeCreateKeysAndCertificateError(const UnicodeString aPayloadFormat = 'json');
void __fastcall RegisterThing(const UnicodeString aTemplateName, const UnicodeString aPayload, const UnicodeString aPayloadFormat = 'json');
void __fastcall SubscribeRegisterThingResponse(const UnicodeString aTemplateName, const UnicodeString aPayloadFormat = 'json');
void __fastcall SubscribeRegisterThingError(const UnicodeString aTemplateName, const UnicodeString aPayloadFormat = 'json');
void __fastcall Subscribe(const UnicodeString aTopic, TawsIoTQoS * aQoS = awsIoTQoS0);
void __fastcall Publish(const UnicodeString aTopic, const UnicodeString aText, TawsIoTQoS * aQoS = awsIoTQoS0);
void __fastcall UnSubscribe(const UnicodeString aTopic);
bool __fastcall PublishAndWait(const UnicodeString aTopic, const UnicodeString aText, TmqttQoS * aQoS = mtqsAtMostOnce, bool aRetain = False, const int aTimeout = 10000);
bool __fastcall Disconnect(int aTimeout = 10000);
```

