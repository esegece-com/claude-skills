# TIdNetworkCalculator

unit: IdNetworkCalculator

Add `IdNetworkCalculator` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `ListIP: TStrings (read-only)` | `TStrings` | `__property TStrings * ListIP /* read-only */;` |
| `NetworkClass: TNetworkClass (read-only)` | [TNetworkClass](../types/TNetworkClass.md) | `__property TNetworkClass * NetworkClass /* read-only */;` |
| `NetworkClassAsString: String (read-only)` | `String` | `__property UnicodeString NetworkClassAsString /* read-only */;` |
| `IsAddressRoutable: Boolean (read-only)` | `Boolean` | `__property bool IsAddressRoutable /* read-only */;` |
| `NetworkAddress: TIpProperty` | [TIpProperty](../types/TIpProperty.md) | `__property TIpProperty * NetworkAddress;` |
| `NetworkMask: TIpProperty` | [TIpProperty](../types/TIpProperty.md) | `__property TIpProperty * NetworkMask;` |
| `NetworkMaskLength: UInt32` | `UInt32` | `__property UInt32 NetworkMaskLength;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnGenIPList: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnGenIPList;` |
| `OnChange: TNotifyEvent` | `TNotifyEvent` | `__property TNotifyEvent OnChange;` |

## Methods

Delphi

```pascal
function IsAddressInNetwork(const Address: String): Boolean;
function NumIP: UInt32;
function StartIP: String;
function EndIP: String;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
bool __fastcall IsAddressInNetwork(const UnicodeString Address);
UInt32 __fastcall NumIP();
UnicodeString __fastcall StartIP();
UnicodeString __fastcall EndIP();
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

