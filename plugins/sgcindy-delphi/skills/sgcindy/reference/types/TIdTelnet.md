# TIdTelnet

kind: class
unit: IdTelnet

## Properties

| Delphi | Type |
| --- | --- |
| `TelnetThread: TIdTelnetReadThread (read-only)` | `TIdTelnetReadThread` |
| `Host: String` | `String` |
| `Port: TIdPort` | `TIdPort` |
| `Terminal: string` | `string` |
| `ThreadedEvent: Boolean` | `Boolean` |
| `BoundIP: string` | `string` |
| `BoundPort: TIdPort` | `TIdPort` |
| `BoundPortMax: TIdPort` | `TIdPort` |
| `BoundPortMin: TIdPort` | `TIdPort` |
| `ConnectTimeout: Integer` | `Integer` |
| `ReadTimeout: Integer` | `Integer` |
| `ReuseSocket: TIdReuseSocket` | `TIdReuseSocket` |
| `UseNagle: Boolean` | `Boolean` |
| `LingerState: Integer` | `Integer` |
| `Greeting: TIdReply` | `TIdReply` |
| `LastCmdResult: TIdReply (read-only)` | `TIdReply` |
| `ManagedIOHandler: Boolean` | `Boolean` |
| `Socket: TIdIOHandlerSocket (read-only)` | `TIdIOHandlerSocket` |
| `Intercept: TIdConnectionIntercept` | `TIdConnectionIntercept` |
| `IOHandler: TIdIOHandler` | `TIdIOHandler` |
| `WorkTarget: TIdComponent` | `TIdComponent` |
| `Version: string (read-only)` | `string` |

## Events

| Delphi | Type |
| --- | --- |
| `OnTelnetCommand: TIdTelnetCommandEvent` | `TIdTelnetCommandEvent` |
| `OnDataAvailable: TIdTelnetDataAvailEvent` | `TIdTelnetDataAvailEvent` |
| `OnBeforeBind: TNotifyEvent` | `TNotifyEvent` |
| `OnAfterBind: TNotifyEvent` | `TNotifyEvent` |
| `OnSocketAllocated: TNotifyEvent` | `TNotifyEvent` |
| `OnConnected: TNotifyEvent` | `TNotifyEvent` |
| `OnDisconnected: TNotifyEvent` | `TNotifyEvent` |
| `OnWork: TWorkEvent` | `TWorkEvent` |
| `OnWorkBegin: TWorkBeginEvent` | `TWorkBeginEvent` |
| `OnWorkEnd: TWorkEndEvent` | `TWorkEndEvent` |
| `OnStatus: TIdStatusEvent` | `TIdStatusEvent` |

## Methods

```pascal
procedure Connect;
procedure Disconnect(ANotifyPeer: Boolean);
procedure SendCh(Ch: Char);
procedure SendString(const S: String);
function ConnectAndGetAll: string;
procedure CreateIOHandler(ABaseType: TIdIOHandlerClass = nil);
procedure CheckForGracefulDisconnect(ARaiseExceptionIfDisconnected: Boolean = True);
function CheckResponse(const AResponse: Int16; const AAllowedResponses: array of Int16): Int16;
function Connected: Boolean;
procedure DisconnectNotifyPeer;
procedure GetInternalResponse(AEncoding: IIdTextEncoding = nil);
function GetResponse(const AAllowedResponse: Int16 = -1; AEncoding: IIdTextEncoding = nil): Int16;
procedure RaiseExceptionForLastCmdResult;
function SendCmd(AOut: string; const AResponse: Int16 = -1; AEncoding: IIdTextEncoding = nil): Int16;
procedure WriteHeader(AHeader: TStrings);
procedure WriteRFCStrings(AStrings: TStrings);
procedure BeginWork(AWorkMode: TWorkMode; const ASize: Int64 = 0);
procedure DoWork(AWorkMode: TWorkMode; const ACount: Int64);
procedure EndWork(AWorkMode: TWorkMode);
procedure RemoveFreeNotification(AComponent: TComponent);
```

