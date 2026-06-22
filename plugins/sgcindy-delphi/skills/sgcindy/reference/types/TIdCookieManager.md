# TIdCookieManager

kind: class
unit: IdCookieManager

## Properties

| Delphi | Type |
| --- | --- |
| `CookieCollection: TIdCookies (read-only)` | [TIdCookies](./TIdCookies.md) |
| `Version: string (read-only)` | `string` |

## Events

| Delphi | Type |
| --- | --- |
| `OnCreate: TOnCookieCreateEvent` | `TOnCookieCreateEvent` |
| `OnDestroy: TOnCookieDestroyEvent` | `TOnCookieDestroyEvent` |
| `OnNewCookie: TOnNewCookieEvent` | [TOnNewCookieEvent](./TOnNewCookieEvent.md) |

## Methods

```pascal
procedure AddServerCookie(const ACookie: String; AURL: TIdURI);
procedure AddServerCookies(const ACookies: TStrings; AURL: TIdURI);
procedure AddCookies(ASource: TIdCookieManager);
procedure CopyCookie(ACookie: TIdCookie);
procedure GenerateClientCookies(AURL: TIdURI; SecureOnly: Boolean; Headers: TIdHeaderList);
procedure RemoveFreeNotification(AComponent: TComponent);
```

