# TIdCookie

kind: class
unit: IdCookie

## Properties

| Delphi | Type |
| --- | --- |
| `ClientCookie: String (read-only)` | `String` |
| `CookieName: String` | `String` |
| `CookieText: String (read-only)` | `String` |
| `Domain: String` | `String` |
| `Expires: TDateTime` | `TDateTime` |
| `HttpOnly: Boolean` | `Boolean` |
| `Path: String` | `String` |
| `Secure: Boolean` | `Boolean` |
| `ServerCookie: String (read-only)` | `String` |
| `Value: String` | `String` |
| `MaxAge: Int64 (read-only)` | `Int64` |
| `CreatedAt: TDateTime` | `TDateTime` |
| `IsExpired: Boolean (read-only)` | `Boolean` |
| `HostOnly: Boolean` | `Boolean` |
| `LastAccessed: TDateTime` | `TDateTime` |
| `Persistent: Boolean` | `Boolean` |
| `SameSite: String` | `String` |

## Methods

```pascal
procedure Assign(Source: TPersistent);
function IsAllowed(AURI: TIdURI; SecureOnly: Boolean): Boolean;
function ParseClientCookie(const ACookieText: String): Boolean;
function ParseServerCookie(const ACookieText: String; AURI: TIdURI): Boolean;
```

