# TsgcRoomList

kind: class
unit: sgcWebSocket_Protocol_AppRTC_Server

## Properties

| Delphi | Type |
| --- | --- |
| `Duplicates: TDuplicates` | `TDuplicates` |
| `IsEmpty: Boolean (read-only)` | `Boolean` |
| `ListType: TsgcThreadListType` | [TsgcThreadListType](./TsgcThreadListType.md) |

## Methods

```pascal
procedure FreeObjects;
procedure Add(Item: Pointer);
procedure AddKey(Item: Pointer; const aKey: String);
procedure Delete(Index: Integer);
procedure DeleteKey(Index: Integer; const aKey: String);
function GetValue(const aKey: String): TObject;
procedure Clear;
function LockList: TList;
procedure Remove(Item: Pointer);
procedure RemoveItem(Item: Pointer; Direction: TList.TDirection);
procedure UnlockList;
```

