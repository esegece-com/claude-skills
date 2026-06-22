# TIdEmailAddressList

kind: class
unit: IdEMailAddress

## Properties

| Delphi | Type |
| --- | --- |
| `Items[Index[Index: Integer]: TIdEMailAddressItem` | [TIdEMailAddressItem](./TIdEMailAddressItem.md) |
| `EMailAddresses: string` | `string` |

## Methods

```pascal
procedure FillTStrings(AStrings: TStrings);
function Add: TIdEMailAddressItem;
procedure AddItems(AList: TIdEMailAddressList);
procedure GetDomains(AStrings: TStrings);
procedure SortByDomain;
procedure AddressesByDomain(AList: TIdEMailAddressList; const ADomain: string);
```

