# TIdCookies

kind: class
unit: IdCookie

## Properties

| Delphi | Type |
| --- | --- |
| `Cookie[const[const AName, ADomain: string]: TIdCookie (read-only)` | [TIdCookie](./TIdCookie.md) |
| `Cookies[Index[Index: Integer]: TIdCookie` | [TIdCookie](./TIdCookie.md) |

## Methods

```pascal
function Add: TIdCookie;
function AddCookie(ACookie: TIdCookie; AURI: TIdURI; AReplaceOld: Boolean = True): Boolean;
function AddClientCookie(const ACookie: string): TIdCookie;
procedure AddClientCookies(const ACookie: string);
function AddServerCookie(const ACookie: string; AURI: TIdURI): TIdCookie;
procedure AddServerCookies(const ACookies: TStrings; AURI: TIdURI);
procedure AddCookies(ASource: TIdCookies);
procedure Assign(ASource: TPersistent);
procedure Clear;
function GetCookieIndex(const AName: string; FirstIndex: Integer = 0): Integer;
function LockCookieList(AAccessType: TIdCookieAccess): TIdCookieList;
procedure UnlockCookieList(AAccessType: TIdCookieAccess);
```

