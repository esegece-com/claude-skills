# TsgcWebView2CookieManager

kind: class
unit: sgcWebView2_Classes

## Properties

| Delphi | Type |
| --- | --- |
| `CookieManager: ICoreWebView2CookieManager (read-only)` | [ICoreWebView2CookieManager](./ICoreWebView2CookieManager.md) |

## Methods

```pascal
procedure GetCookies(const aURI: string);
procedure AddOrUpdateCookie(const aName, aValue, aDomain, aPath: string);
procedure DeleteCookie(const aName, aURI: string);
procedure DeleteAllCookies;
procedure DeleteCookiesWithDomainAndPath(const aDomain, aPath: string);
```

