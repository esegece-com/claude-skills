# TsgcWSServerGroups

kind: class
unit: sgcWebSocket_Server_Groups

## Properties

| Delphi | Type |
| --- | --- |
| `Group[const[const aName: String]: TsgcWSServerGroupItem (read-only)` | [TsgcWSServerGroupItem](./TsgcWSServerGroupItem.md) |
| `Item[Index[Index: Integer]: TsgcQueueItemBase (read-only)` | [TsgcQueueItemBase](./TsgcQueueItemBase.md) |
| `Count: Integer (read-only)` | `Integer` |
| `OwnObjects: Boolean` | `Boolean` |
| `Duplicates: TDuplicates` | `TDuplicates` |
| `IsEmpty: Boolean (read-only)` | `Boolean` |
| `ListType: TsgcThreadListType` | [TsgcThreadListType](./TsgcThreadListType.md) |

## Events

| Delphi | Type |
| --- | --- |
| `OnClientAdded: TsgcWSServerGroupClientAddedEvent` | [TsgcWSServerGroupClientAddedEvent](./TsgcWSServerGroupClientAddedEvent.md) |
| `OnClientRemoved: TsgcWSServerGroupClientRemovedEvent` | [TsgcWSServerGroupClientRemovedEvent](./TsgcWSServerGroupClientRemovedEvent.md) |

## Methods

```pascal
function Add(const aGroupName: string; const aConnection: TsgcWSConnection): Boolean;
procedure Remove(const aConnection: TsgcWSConnection);
procedure BroadCast(const aGroupMask, aMessage: string);
procedure SortByOrder(aAscending: Boolean = True);
procedure AddItem(const aItem: TsgcQueueItemBase);
function DeleteItem(const aID: String): Boolean;
function GetItem(const aID: String): TsgcQueueItemBase;
procedure Clear;
procedure AddKey(Item: Pointer; const aKey: String);
procedure Delete(Index: Integer);
procedure DeleteKey(Index: Integer; const aKey: String);
function GetValue(const aKey: String): TObject;
function LockList: TList;
procedure RemoveItem(Item: Pointer; Direction: TList.TDirection);
procedure UnlockList;
```

