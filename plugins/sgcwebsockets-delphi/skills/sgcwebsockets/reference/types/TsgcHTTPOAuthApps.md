# TsgcHTTPOAuthApps

kind: class
unit: sgcHTTP_OAuth_Server

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
procedure AddApp(const aName, aRedirectURI, aClientId, aClientSecret: string; const aExpiresIn: Integer = 3600; const aRefreshToken: Boolean = True; const aAllowedGrantTypes: TsgcOAuth2AllowedGrantTypes = [auth2Code, auth2ClientCredentials]);
function RemoveApp(const aName: string): Boolean;
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

