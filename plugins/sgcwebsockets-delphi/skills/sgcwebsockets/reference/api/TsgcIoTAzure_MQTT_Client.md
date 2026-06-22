# TsgcIoTAzure_MQTT_Client

unit: sgcIoT
Edition: Standard

Add `sgcIoT` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `Certificate: PX509 (read-only)` | `PX509` | `__property PX509 Certificate /* read-only */;` |
| `SAS: TsgcIoTComponent_Client_SAS` | [TsgcIoTComponent_Client_SAS](../types/TsgcIoTComponent_Client_SAS.md) | `__property TsgcIoTComponent_Client_SAS * SAS;` |
| `Azure: TsgcIoT_Azure_MQTT_Client_Options` | [TsgcIoT_Azure_MQTT_Client_Options](../types/TsgcIoT_Azure_MQTT_Client_Options.md) | `__property TsgcIoT_Azure_MQTT_Client_Options * Azure;` |
| `MQTTHeartBeat: TsgcWSMQTTHeartBeat_Options` | [TsgcWSMQTTHeartBeat_Options](../types/TsgcWSMQTTHeartBeat_Options.md) | `__property TsgcWSMQTTHeartBeat_Options * MQTTHeartBeat;` |
| `WatchDog: TsgcWSWatchDogClient_Options` | [TsgcWSWatchDogClient_Options](../types/TsgcWSWatchDogClient_Options.md) | `__property TsgcWSWatchDogClient_Options * WatchDog;` |
| `LogFile: TsgcAWSLogFile` | [TsgcAWSLogFile](../types/TsgcAWSLogFile.md) | `__property TsgcAWSLogFile * LogFile;` |
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
procedure ReadConnectionString(const aValue: string);
function Subscribe_CloudToDevice: Integer;
function UnSubscribe_CloudToDevice: Integer;
function Send_DeviceToCloud(const aText: String; aQoS: TazuIoTQoS = azuIoTQoS0): Integer;
function SendAndWait_DeviceToCloud(const aText: String; const aTimeout: Integer = 10000): Boolean;
function Subscribe_DeviceTwins: Integer;
function UnSubscribe_DeviceTwins: Integer;
procedure Get_DeviceTwinsProperties(const aRequestId: string; aQoS: TazuIoTQoS = azuIoTQoS0);
function GetAndWait_DeviceTwinsProperties(const aRequestId: string; const aTimeout: Integer = 10000): Boolean;
function Set_DeviceTwinsProperties(const aRequestId: string; aText: String; aQoS: TazuIoTQoS = azuIoTQoS0): Integer;
function SetAndWait_DeviceTwinsProperties(const aRequestId: string; aText: String; const aTimeout: Integer = 10000): Boolean;
function Subscribe_DirectMethod: Integer;
function UnSubscribe_DirectMethod: Integer;
function RespondPublicMethod(const aRequestId: string; aStatus: Integer; const aText: String; aQoS: TazuIoTQoS = azuIoTQoS0): Integer;
function RespondAndWaitPublicMethod(const aRequestId: string; aStatus: Integer; const aText: String; const aTimeout: Integer = 10000): Boolean;
procedure UploadFile(const aFileName: string; aOverwrite: Boolean = False);
procedure UploadStream(const aFileName: string; const aStream: TStream; aOverwrite: Boolean = False);
function ProvisioningDeviceClient_Register(const aScopeId, aRegistrationId : string; var Response: TsgcIoT_Azure_OperationRegistrationState; aTimeout: Integer = 10000): Boolean;
procedure Subscribe(const aTopic: String);
procedure UnSubscribe(const aTopic: String);
function Publish(const aTopic, aText: String; aQoS: TmqttQoS = mtqsAtMostOnce; aRetain: Boolean = False): integer;
function PublishAndWait(const aTopic, aText: String; aQoS: TmqttQoS = mtqsAtMostOnce; aRetain: Boolean = False; const aTimeout: integer = 10000): Boolean;
function Disconnect(aTimeout: Integer = 10000): Boolean;
```

C++Builder

```cpp
void __fastcall ReadConnectionString(const UnicodeString aValue);
int __fastcall Subscribe_CloudToDevice();
int __fastcall UnSubscribe_CloudToDevice();
int __fastcall Send_DeviceToCloud(const UnicodeString aText, TazuIoTQoS * aQoS = azuIoTQoS0);
bool __fastcall SendAndWait_DeviceToCloud(const UnicodeString aText, const int aTimeout = 10000);
int __fastcall Subscribe_DeviceTwins();
int __fastcall UnSubscribe_DeviceTwins();
void __fastcall Get_DeviceTwinsProperties(const UnicodeString aRequestId, TazuIoTQoS * aQoS = azuIoTQoS0);
bool __fastcall GetAndWait_DeviceTwinsProperties(const UnicodeString aRequestId, const int aTimeout = 10000);
int __fastcall Set_DeviceTwinsProperties(const UnicodeString aRequestId, UnicodeString aText, TazuIoTQoS * aQoS = azuIoTQoS0);
bool __fastcall SetAndWait_DeviceTwinsProperties(const UnicodeString aRequestId, UnicodeString aText, const int aTimeout = 10000);
int __fastcall Subscribe_DirectMethod();
int __fastcall UnSubscribe_DirectMethod();
int __fastcall RespondPublicMethod(const UnicodeString aRequestId, int aStatus, const UnicodeString aText, TazuIoTQoS * aQoS = azuIoTQoS0);
bool __fastcall RespondAndWaitPublicMethod(const UnicodeString aRequestId, int aStatus, const UnicodeString aText, const int aTimeout = 10000);
void __fastcall UploadFile(const UnicodeString aFileName, bool aOverwrite = False);
void __fastcall UploadStream(const UnicodeString aFileName, const TStream * aStream, bool aOverwrite = False);
bool __fastcall ProvisioningDeviceClient_Register(const UnicodeString aScopeId, const UnicodeString aRegistrationId, TsgcIoT_Azure_OperationRegistrationState * &Response, int aTimeout = 10000);
void __fastcall Subscribe(const UnicodeString aTopic);
void __fastcall UnSubscribe(const UnicodeString aTopic);
int __fastcall Publish(const UnicodeString aTopic, const UnicodeString aText, TmqttQoS * aQoS = mtqsAtMostOnce, bool aRetain = False);
bool __fastcall PublishAndWait(const UnicodeString aTopic, const UnicodeString aText, TmqttQoS * aQoS = mtqsAtMostOnce, bool aRetain = False, const int aTimeout = 10000);
bool __fastcall Disconnect(int aTimeout = 10000);
```

