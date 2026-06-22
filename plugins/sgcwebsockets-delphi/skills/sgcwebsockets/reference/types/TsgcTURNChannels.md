# TsgcTURNChannels

kind: class
unit: sgcP2P_TURN_Classes

## Properties

| Delphi | Type |
| --- | --- |
| `Lifetime: Integer` | `Integer` |
| `MinChannelID: Word` | `Word` |
| `MaxChannelID: Word` | `Word` |
| `Item[Index[Index: Integer]: TsgcQueueItemBase (read-only)` | `TsgcQueueItemBase` |
| `Count: Integer (read-only)` | `Integer` |
| `OwnObjects: Boolean` | `Boolean` |
| `Duplicates: TDuplicates` | `TDuplicates` |
| `IsEmpty: Boolean (read-only)` | `Boolean` |
| `ListType: TsgcThreadListType` | `TsgcThreadListType` |

## Methods

```pascal
function CreateChannel(const aIPAddress: string; aPort: Word; const aChannelID: Word = 0): TsgcTURNChannel;
function CreateUpdateChannel(const aIPAddress: string; aPort: Word; const aChannelID: Word = 0): TsgcTURNChannel;
function GetChannel(const aIPAddress: string; aPort: Word) : TsgcTURNChannel;
function IsValidChannel(const aIPAddress: string; aPort: Word): Boolean;
function DeleteChannel(const aChannelID: Word): Boolean;
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

