# TIdMailBox

kind: class
unit: IdMailBox

## Properties

| Delphi | Type |
| --- | --- |
| `Attributes: TIdMailBoxAttributes` | [TIdMailBoxAttributes](./TIdMailBoxAttributes.md) |
| `ChangeableFlags: TIdMessageFlagsSet` | `TIdMessageFlagsSet` |
| `FirstUnseenMsg: UInt32` | `UInt32` |
| `Flags: TIdMessageFlagsSet` | `TIdMessageFlagsSet` |
| `Name: String` | `String` |
| `MessageList: TIdMessageCollection` | [TIdMessageCollection](./TIdMessageCollection.md) |
| `RecentMsgs: Integer` | `Integer` |
| `State: TIdMailBoxState` | [TIdMailBoxState](./TIdMailBoxState.md) |
| `TotalMsgs: Integer` | `Integer` |
| `UIDNext: String` | `String` |
| `UIDValidity: String` | `String` |
| `UnseenMsgs: Integer` | `Integer` |
| `Version: string (read-only)` | `string` |

## Methods

```pascal
procedure Clear;
procedure RemoveFreeNotification(AComponent: TComponent);
```

