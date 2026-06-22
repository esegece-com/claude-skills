# TsgcWebPushSubscriptions

kind: class
unit: sgcWebSocket_Server_API_WebPush

## Properties

| Delphi | Type |
| --- | --- |
| `Item[Index[Index: Integer]: TsgcQueueItemBase (read-only)` | [TsgcQueueItemBase](./TsgcQueueItemBase.md) |
| `Count: Integer (read-only)` | `Integer` |
| `OwnObjects: Boolean` | `Boolean` |
| `Duplicates: TDuplicates` | `TDuplicates` |
| `IsEmpty: Boolean (read-only)` | `Boolean` |
| `ListType: TsgcThreadListType` | [TsgcThreadListType](./TsgcThreadListType.md) |

## Methods

```pascal
procedure AddSubscription(const aSubscription : TsgcHTTP_API_WebPush_PushSubscription);
procedure RemoveSubscription(const aSubscription : TsgcHTTP_API_WebPush_PushSubscription);
procedure SortByOrder(aAscending: Boolean = True);
procedure AddItem(const aItem: TsgcQueueItemBase);
function DeleteItem(const aID: String): Boolean;
function GetItem(const aID: String): TsgcQueueItemBase;
procedure Clear;
procedure Add(Item: Pointer);
procedure AddKey(Item: Pointer; const aKey: String);
procedure Delete(Index: Integer);
procedure DeleteKey(Index: Integer; const aKey: String);
function GetValue(const aKey: String): TObject;
function LockList: TList;
procedure Remove(Item: Pointer);
procedure RemoveItem(Item: Pointer; Direction: TList.TDirection);
procedure UnlockList;
```

