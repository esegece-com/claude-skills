# TsgcAMQPChannelThreads

kind: class
unit: sgcAMQP_Classes

## Properties

| Delphi | Type |
| --- | --- |
| `Item[Index[Index: Integer]: TsgcQueueItemBase (read-only)` | [TsgcQueueItemBase](./TsgcQueueItemBase.md) |
| `Count: Integer (read-only)` | `Integer` |
| `OwnObjects: Boolean` | `Boolean` |
| `Duplicates: TDuplicates` | `TDuplicates` |
| `IsEmpty: Boolean (read-only)` | `Boolean` |
| `ListType: TsgcThreadListType` | [TsgcThreadListType](./TsgcThreadListType.md) |

## Events

| Delphi | Type |
| --- | --- |
| `OnException: TsgcAMQPThreadExceptionEvent` | [TsgcAMQPThreadExceptionEvent](./TsgcAMQPThreadExceptionEvent.md) |

## Methods

```pascal
procedure AddFrame(const aFrame: TsgcAMQPFrame);
function AddChannel(const aChannel: string): Word;
function GetChannel(const aChannel: string) : TsgcAMQPChannelThreadItem;
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

