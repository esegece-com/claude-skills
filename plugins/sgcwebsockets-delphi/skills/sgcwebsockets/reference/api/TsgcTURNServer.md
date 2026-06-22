# TsgcTURNServer

unit: sgcP2P
Edition: Enterprise

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
| `TURNOptions: TsgcTURNServer_Options` | [TsgcTURNServer_Options](../types/TsgcTURNServer_Options.md) | `__property TsgcTURNServer_Options * TURNOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `Bindings: TIdSocketHandles` | [TIdSocketHandles](../types/TIdSocketHandles.md) | `__property TIdSocketHandles * Bindings;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnSTUNException: TsgcSTUNExceptionEvent` | [TsgcSTUNExceptionEvent](../types/TsgcSTUNExceptionEvent.md) | `__property TsgcSTUNExceptionEvent OnSTUNException;` |
| `OnSTUNRequestError: TsgcSTUNRequestErrorEvent` | [TsgcSTUNRequestErrorEvent](../types/TsgcSTUNRequestErrorEvent.md) | `__property TsgcSTUNRequestErrorEvent OnSTUNRequestError;` |
| `OnSTUNRequestSuccess: TsgcSTUNRequestSuccessEvent` | [TsgcSTUNRequestSuccessEvent](../types/TsgcSTUNRequestSuccessEvent.md) | `__property TsgcSTUNRequestSuccessEvent OnSTUNRequestSuccess;` |
| `OnSTUNRequestAuthorization: TsgcSTUNRequestAuthorizationEvent` | [TsgcSTUNRequestAuthorizationEvent](../types/TsgcSTUNRequestAuthorizationEvent.md) | `__property TsgcSTUNRequestAuthorizationEvent OnSTUNRequestAuthorization;` |
| `OnTURNBeforeAllocate: TsgcTURNBeforeAllocateEvent` | [TsgcTURNBeforeAllocateEvent](../types/TsgcTURNBeforeAllocateEvent.md) | `__property TsgcTURNBeforeAllocateEvent OnTURNBeforeAllocate;` |
| `OnTURNBeforeRelayIndication: TsgcTURNBeforeRelayIndicationEvent` | [TsgcTURNBeforeRelayIndicationEvent](../types/TsgcTURNBeforeRelayIndicationEvent.md) | `__property TsgcTURNBeforeRelayIndicationEvent OnTURNBeforeRelayIndication;` |
| `OnTURNBeforeRelayChannelData: TsgcTURNBeforeRelayChannelDataEvent` | [TsgcTURNBeforeRelayChannelDataEvent](../types/TsgcTURNBeforeRelayChannelDataEvent.md) | `__property TsgcTURNBeforeRelayChannelDataEvent OnTURNBeforeRelayChannelData;` |
| `OnTURNChannelDataDiscarded: TsgcTURNChannelDataDiscardedEvent` | [TsgcTURNChannelDataDiscardedEvent](../types/TsgcTURNChannelDataDiscardedEvent.md) | `__property TsgcTURNChannelDataDiscardedEvent OnTURNChannelDataDiscarded;` |
| `OnTURNMessageDiscarded: TsgcTURNMessageDiscardedEvent` | [TsgcTURNMessageDiscardedEvent](../types/TsgcTURNMessageDiscardedEvent.md) | `__property TsgcTURNMessageDiscardedEvent OnTURNMessageDiscarded;` |
| `OnTURNCreateAllocation: TsgcTURNAllocationEvent` | [TsgcTURNAllocationEvent](../types/TsgcTURNAllocationEvent.md) | `__property TsgcTURNAllocationEvent OnTURNCreateAllocation;` |
| `OnTURNDeleteAllocation: TsgcTURNAllocationEvent` | [TsgcTURNAllocationEvent](../types/TsgcTURNAllocationEvent.md) | `__property TsgcTURNAllocationEvent OnTURNDeleteAllocation;` |

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

