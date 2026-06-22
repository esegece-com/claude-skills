# TsgcQueueListChannels

kind: class
unit: sgcWebSocket_Classes

## Properties

| Delphi | Type |
| --- | --- |
| `Count: Integer (read-only)` | `Integer` |
| `OwnObjects: Boolean` | `Boolean` |
| `Duplicates: TDuplicates` | `TDuplicates` |
| `IsEmpty: Boolean (read-only)` | `Boolean` |
| `ListType: TsgcThreadListType` | [TsgcThreadListType](./TsgcThreadListType.md) |

## Methods

```pascal
procedure GetConnections(const aChannel: String; var aList: TList<TsgcWSConnection>);
procedure GetChannels(const aID: String; var aList: TList<TsgcQueueItemChannel>);
function AddItem(const aItem: TsgcQueueNameItemBase): Boolean;
procedure DeleteItem(const aID: String);
function GetQueueByName(const aQueueName: String): TsgcQueueNameBase;
function GetQueuesDelimitedText: String;
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

