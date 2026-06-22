# TIdCookieManager

unit: IdCookieManager

Add `IdCookieManager` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `CookieCollection: TIdCookies (read-only)` | [TIdCookies](../types/TIdCookies.md) | `__property TIdCookies * CookieCollection /* read-only */;` |
| `Version: string (read-only)` | `string` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnCreate: TOnCookieCreateEvent` | `TOnCookieCreateEvent` | `__property TOnCookieCreateEvent OnCreate;` |
| `OnDestroy: TOnCookieDestroyEvent` | `TOnCookieDestroyEvent` | `__property TOnCookieDestroyEvent OnDestroy;` |
| `OnNewCookie: TOnNewCookieEvent` | [TOnNewCookieEvent](../types/TOnNewCookieEvent.md) | `__property TOnNewCookieEvent OnNewCookie;` |

## Methods

Delphi

```pascal
procedure AddServerCookie(const ACookie: String; AURL: TIdURI);
procedure AddServerCookies(const ACookies: TStrings; AURL: TIdURI);
procedure AddCookies(ASource: TIdCookieManager);
procedure CopyCookie(ACookie: TIdCookie);
procedure GenerateClientCookies(AURL: TIdURI; SecureOnly: Boolean; Headers: TIdHeaderList);
procedure RemoveFreeNotification(AComponent: TComponent);
```

C++Builder

```cpp
void __fastcall AddServerCookie(const UnicodeString ACookie, TIdURI * AURL);
void __fastcall AddServerCookies(const TStrings * ACookies, TIdURI * AURL);
void __fastcall AddCookies(TIdCookieManager * ASource);
void __fastcall CopyCookie(TIdCookie * ACookie);
void __fastcall GenerateClientCookies(TIdURI * AURL, bool SecureOnly, TIdHeaderList * Headers);
void __fastcall RemoveFreeNotification(TComponent * AComponent);
```

