# TsgcWebSocketClient_WinHTTP

unit: sgcWebSocket
Edition: Standard

Add `sgcWebSocket` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `Host: String` | `String` | `__property UnicodeString Host;` |
| `Port: Integer` | `Integer` | `__property int Port;` |
| `URL: String` | `String` | `__property UnicodeString URL;` |
| `ConnectTimeout: Integer` | `Integer` | `__property int ConnectTimeout;` |
| `ReadTimeout: Integer` | `Integer` | `__property int ReadTimeout;` |
| `HeartBeat: TsgcWSHeartBeat_Options` | [TsgcWSHeartBeat_Options](../types/TsgcWSHeartBeat_Options.md) | `__property TsgcWSHeartBeat_Options * HeartBeat;` |
| `TLS: Boolean` | `Boolean` | `__property bool TLS;` |
| `TLSOptions: TsgcTLSOptions_Winhttp` | [TsgcTLSOptions_Winhttp](../types/TsgcTLSOptions_Winhttp.md) | `__property TsgcTLSOptions_Winhttp * TLSOptions;` |
| `Authentication: TsgcWSAuthenticationClient_Options` | [TsgcWSAuthenticationClient_Options](../types/TsgcWSAuthenticationClient_Options.md) | `__property TsgcWSAuthenticationClient_Options * Authentication;` |
| `Asynchronous: Boolean` | `Boolean` | `__property bool Asynchronous;` |
| `Proxy: TsgcWSProxy_Options` | [TsgcWSProxy_Options](../types/TsgcWSProxy_Options.md) | `__property TsgcWSProxy_Options * Proxy;` |
| `Options: TsgcWSOptionsClient` | [TsgcWSOptionsClient](../types/TsgcWSOptionsClient.md) | `__property TsgcWSOptionsClient * Options;` |
| `NotifyEvents: TwsNotifyEvent` | [TwsNotifyEvent](../types/TwsNotifyEvent.md) | `__property TwsNotifyEvent NotifyEvents;` |
| `WatchDog: TsgcWSWatchDogClient_Options` | [TsgcWSWatchDogClient_Options](../types/TsgcWSWatchDogClient_Options.md) | `__property TsgcWSWatchDogClient_Options * WatchDog;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `ReceiveBufferSize: Integer` | `Integer` | `__property int ReceiveBufferSize;` |
| `BoundIP: string` | `string` | `__property UnicodeString BoundIP;` |
| `BoundPort: TIdPort` | `TIdPort` | `__property TIdPort * BoundPort;` |
| `BoundPortMax: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMax;` |
| `BoundPortMin: TIdPort` | `TIdPort` | `__property TIdPort * BoundPortMin;` |
| `FreeConnectionOnDestroy: Boolean` | `Boolean` | `__property bool FreeConnectionOnDestroy;` |
| `Specifications: TsgcWSSpecifications` | [TsgcWSSpecifications](../types/TsgcWSSpecifications.md) | `__property TsgcWSSpecifications * Specifications;` |
| `LogFile: TsgcWSLogFile` | [TsgcWSLogFile](../types/TsgcWSLogFile.md) | `__property TsgcWSLogFile * LogFile;` |
| `TCPKeepAlive: TsgcTCPKeepAlive` | [TsgcTCPKeepAlive](../types/TsgcTCPKeepAlive.md) | `__property TsgcTCPKeepAlive * TCPKeepAlive;` |
| `Extensions: TsgcWSExtensions` | [TsgcWSExtensions](../types/TsgcWSExtensions.md) | `__property TsgcWSExtensions * Extensions;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |
| `OnBeforeWatchDog: TsgcWSOnBeforeWatchDogEvent` | [TsgcWSOnBeforeWatchDogEvent](../types/TsgcWSOnBeforeWatchDogEvent.md) | `__property TsgcWSOnBeforeWatchDogEvent OnBeforeWatchDog;` |
| `OnBeforeConnect: TsgcWSOnBeforeConnectEvent` | [TsgcWSOnBeforeConnectEvent](../types/TsgcWSOnBeforeConnectEvent.md) | `__property TsgcWSOnBeforeConnectEvent OnBeforeConnect;` |
| `OnHandshake: TsgcWSHandshakeEvent` | [TsgcWSHandshakeEvent](../types/TsgcWSHandshakeEvent.md) | `__property TsgcWSHandshakeEvent OnHandshake;` |

## Methods

Delphi

```pascal
procedure WriteData(const aText: String; const aSize: Integer = 0; const aStreaming: TwsStreaming = stmNone);
function WriteAndWaitData(const aText: String; const aTimeout: Integer = 10000): string;
procedure Start;
procedure Stop;
function Connect(const aTimeout: Integer = 10000): Boolean;
function Disconnect(const aTimeout: Integer = 10000): Boolean;
procedure Ping;
function CheckPlatform: Boolean;
procedure RegisterProtocol(aObject: TsgcWSProtocol);
procedure UnRegisterProtocol(aObject: TsgcWSProtocol);
procedure RegisterAPI(aObject: TsgcWSAPI);
procedure UnRegisterAPI(aObject: TsgcWSAPI);
procedure EnterCS;
procedure LeaveCS;
function AssignedCS: Boolean;
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall WriteData(const UnicodeString aText, const int aSize = 0, const TwsStreaming * aStreaming = stmNone);
UnicodeString __fastcall WriteAndWaitData(const UnicodeString aText, const int aTimeout = 10000);
void __fastcall Start();
void __fastcall Stop();
bool __fastcall Connect(const int aTimeout = 10000);
bool __fastcall Disconnect(const int aTimeout = 10000);
void __fastcall Ping();
bool __fastcall CheckPlatform();
void __fastcall RegisterProtocol(TsgcWSProtocol * aObject);
void __fastcall UnRegisterProtocol(TsgcWSProtocol * aObject);
void __fastcall RegisterAPI(TsgcWSAPI * aObject);
void __fastcall UnRegisterAPI(TsgcWSAPI * aObject);
void __fastcall EnterCS();
void __fastcall LeaveCS();
bool __fastcall AssignedCS();
void __fastcall QueueClear();
```

