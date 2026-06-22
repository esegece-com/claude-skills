# TsgcHTTP2Request

kind: class
unit: sgcHTTP2_Classes

## Properties

| Delphi | Type |
| --- | --- |
| `Method: Th2Methods` | [Th2Methods](./Th2Methods.md) |
| `URL: String` | `String` |
| `Cookies: TStringList` | `TStringList` |
| `Redirect: Boolean` | `Boolean` |
| `Accept: String` | `String` |
| `AcceptCharSet: String` | `String` |
| `AcceptEncoding: string` | `string` |
| `AcceptLanguage: string` | `string` |
| `BasicAuthentication: Boolean` | `Boolean` |
| `BearerAuthentication: Boolean` | `Boolean` |
| `BearerToken: string` | `string` |
| `CacheControl: string` | `string` |
| `CharSet: string` | `string` |
| `Connection: string` | `string` |
| `ContentDisposition: string` | `string` |
| `ContentType: string` | `string` |
| `ContentVersion: string` | `string` |
| `CustomHeaders: TStringList` | `TStringList` |
| `Date: TDateTime` | `TDateTime` |
| `ETag: string` | `string` |
| `Expires: TDateTime` | `TDateTime` |
| `From: string` | `string` |
| `Host: string` | `string` |
| `ID: String` | `String` |
| `LastModified: TDateTime` | `TDateTime` |
| `Password: string` | `string` |
| `Referer: string` | `string` |
| `TransferEncoding: string` | `string` |
| `UserAgent: string` | `string` |
| `Username: String` | `String` |

## Methods

```pascal
procedure Assign(aSource: TPersistent);
procedure AddCookie(const aName, aValue: String);
procedure ClearCookies;
function GetCookiesHeader: String;
```

