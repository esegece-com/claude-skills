# TsgcSTUNServer

unit: sgcP2P
Edition: Professional and higher

Add `sgcP2P` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `Host: string` | `string` | `__property UnicodeString Host;` |
| `Port: Integer` | `Integer` | `__property int Port;` |
| `IPVersion: TIdIPVersion` | `TIdIPVersion` | `__property TIdIPVersion * IPVersion;` |
| `STUNOptions: TsgcSTUNServer_Options` | [TsgcSTUNServer_Options](../types/TsgcSTUNServer_Options.md) | `__property TsgcSTUNServer_Options * STUNOptions;` |
| `LogFile: TsgcSTUNLogFile` | [TsgcSTUNLogFile](../types/TsgcSTUNLogFile.md) | `__property TsgcSTUNLogFile * LogFile;` |
| `NotifyEvents: TwsNotifyEvent` | [TwsNotifyEvent](../types/TwsNotifyEvent.md) | `__property TwsNotifyEvent NotifyEvents;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `Bindings: TIdSocketHandles` | [TIdSocketHandles](../types/TIdSocketHandles.md) | `__property TIdSocketHandles * Bindings;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnSTUNException: TsgcSTUNExceptionEvent` | [TsgcSTUNExceptionEvent](../types/TsgcSTUNExceptionEvent.md) | `__property TsgcSTUNExceptionEvent OnSTUNException;` |
| `OnSTUNRequestError: TsgcSTUNRequestErrorEvent` | [TsgcSTUNRequestErrorEvent](../types/TsgcSTUNRequestErrorEvent.md) | `__property TsgcSTUNRequestErrorEvent OnSTUNRequestError;` |
| `OnSTUNRequestSuccess: TsgcSTUNRequestSuccessEvent` | [TsgcSTUNRequestSuccessEvent](../types/TsgcSTUNRequestSuccessEvent.md) | `__property TsgcSTUNRequestSuccessEvent OnSTUNRequestSuccess;` |
| `OnSTUNRequestAuthorization: TsgcSTUNRequestAuthorizationEvent` | [TsgcSTUNRequestAuthorizationEvent](../types/TsgcSTUNRequestAuthorizationEvent.md) | `__property TsgcSTUNRequestAuthorizationEvent OnSTUNRequestAuthorization;` |

## Methods

Delphi

```pascal
function AddBinding(const aIPAddress: string; aPort: Integer) : TIdSocketHandle;
function RemoveBinding(const aIPAddress: string; aPort: Integer): Boolean;
```

C++Builder

```cpp
TIdSocketHandle * __fastcall AddBinding(const UnicodeString aIPAddress, int aPort);
bool __fastcall RemoveBinding(const UnicodeString aIPAddress, int aPort);
```

