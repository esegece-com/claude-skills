# TIdHTTPCustomSessionList

kind: class
unit: IdCustomHTTPServer

## Properties

| Delphi | Type |
| --- | --- |
| `SessionTimeout: Integer` | `Integer` |
| `Version: string (read-only)` | `string` |

## Events

| Delphi | Type |
| --- | --- |
| `OnSessionEnd: TIdHTTPSessionEndEvent` | [TIdHTTPSessionEndEvent](./TIdHTTPSessionEndEvent.md) |
| `OnSessionStart: TIdHTTPSessionStartEvent` | [TIdHTTPSessionStartEvent](./TIdHTTPSessionStartEvent.md) |

## Methods

```pascal
procedure Clear;
procedure PurgeStaleSessions(PurgeAll: Boolean = false);
function CreateUniqueSession(const RemoteIP: String): TIdHTTPSession;
function CreateSession(const RemoteIP, SessionID: String): TIdHTTPSession;
function GetSession(const SessionID, RemoteIP: string): TIdHTTPSession;
procedure Add(ASession: TIdHTTPSession);
procedure RemoveFreeNotification(AComponent: TComponent);
```

