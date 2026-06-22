# TIdMailBox

unit: IdMailBox

Add `IdMailBox` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Attributes: TIdMailBoxAttributes` | [TIdMailBoxAttributes](../types/TIdMailBoxAttributes.md) | `__property TIdMailBoxAttributes * Attributes;` |
| `ChangeableFlags: TIdMessageFlagsSet` | `TIdMessageFlagsSet` | `__property TIdMessageFlagsSet * ChangeableFlags;` |
| `FirstUnseenMsg: UInt32` | `UInt32` | `__property UInt32 FirstUnseenMsg;` |
| `Flags: TIdMessageFlagsSet` | `TIdMessageFlagsSet` | `__property TIdMessageFlagsSet * Flags;` |
| `Name: String` | `String` | `__property UnicodeString Name;` |
| `MessageList: TIdMessageCollection` | [TIdMessageCollection](../types/TIdMessageCollection.md) | `__property TIdMessageCollection * MessageList;` |
| `RecentMsgs: Integer` | `Integer` | `__property int RecentMsgs;` |
| `State: TIdMailBoxState` | [TIdMailBoxState](../types/TIdMailBoxState.md) | `__property TIdMailBoxState * State;` |
| `TotalMsgs: Integer` | `Integer` | `__property int TotalMsgs;` |
| `UIDNext: String` | `String` | `__property UnicodeString UIDNext;` |
| `UIDValidity: String` | `String` | `__property UnicodeString UIDValidity;` |
| `UnseenMsgs: Integer` | `Integer` | `__property int UnseenMsgs;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Methods

Delphi

```pascal
procedure Clear;
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall Clear();
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

