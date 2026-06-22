# TsgcHTTP_JWT_Client

unit: sgcHTTP
Edition: Standard

Add `sgcHTTP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `JWTOptions: TsgcHTTP_JWT_Client_Options` | [TsgcHTTP_JWT_Client_Options](../types/TsgcHTTP_JWT_Client_Options.md) | `__property TsgcHTTP_JWT_Client_Options * JWTOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnAuthToken: TsgcOnAuthToken` | [TsgcOnAuthToken](../types/TsgcOnAuthToken.md) | `__property TsgcOnAuthToken * OnAuthToken;` |
| `OnAuthTokenError: TsgcOnAuthTokenError` | [TsgcOnAuthTokenError](../types/TsgcOnAuthTokenError.md) | `__property TsgcOnAuthTokenError * OnAuthTokenError;` |

## Methods

Delphi

```pascal
procedure Start;
function Sign: string;
```

C++Builder

```cpp
void __fastcall Start();
UnicodeString __fastcall Sign();
```

