# TsgcHTTP_JWT_Server

unit: sgcHTTP
Edition: Enterprise

Add `sgcHTTP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `JWTOptions: TsgcHTTP_JWT_Server_Options` | [TsgcHTTP_JWT_Server_Options](../types/TsgcHTTP_JWT_Server_Options.md) | `__property TsgcHTTP_JWT_Server_Options * JWTOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnJWTBeforeRequest: TsgcHTTPJWTBeforeRequestEvent` | [TsgcHTTPJWTBeforeRequestEvent](../types/TsgcHTTPJWTBeforeRequestEvent.md) | `__property TsgcHTTPJWTBeforeRequestEvent OnJWTBeforeRequest;` |
| `OnJWTAfterValidateToken: TsgcHTTPJWTAfterValidateTokenEvent` | [TsgcHTTPJWTAfterValidateTokenEvent](../types/TsgcHTTPJWTAfterValidateTokenEvent.md) | `__property TsgcHTTPJWTAfterValidateTokenEvent OnJWTAfterValidateToken;` |
| `OnJWTBeforeValidateToken: TsgcHTTPJWTBeforeValidateTokenEvent` | [TsgcHTTPJWTBeforeValidateTokenEvent](../types/TsgcHTTPJWTBeforeValidateTokenEvent.md) | `__property TsgcHTTPJWTBeforeValidateTokenEvent OnJWTBeforeValidateToken;` |
| `OnJWTBeforeValidateSignature: TsgcHTTPJWTBeforeValidateSignatureEvent` | [TsgcHTTPJWTBeforeValidateSignatureEvent](../types/TsgcHTTPJWTBeforeValidateSignatureEvent.md) | `__property TsgcHTTPJWTBeforeValidateSignatureEvent OnJWTBeforeValidateSignature;` |
| `OnJWTUnauthorized: TsgcHTTPJWTUnauthorizedEvent` | [TsgcHTTPJWTUnauthorizedEvent](../types/TsgcHTTPJWTUnauthorizedEvent.md) | `__property TsgcHTTPJWTUnauthorizedEvent OnJWTUnauthorized;` |
| `OnJWTException: TsgcHTTPJWTExceptionEvent` | [TsgcHTTPJWTExceptionEvent](../types/TsgcHTTPJWTExceptionEvent.md) | `__property TsgcHTTPJWTExceptionEvent OnJWTException;` |
| `OnJWTResponseError: TsgcHTTPJWTResponseErrorEvent` | [TsgcHTTPJWTResponseErrorEvent](../types/TsgcHTTPJWTResponseErrorEvent.md) | `__property TsgcHTTPJWTResponseErrorEvent OnJWTResponseError;` |

## Methods

Delphi

```pascal
function Validate(const aJWT: string; var aHeader, aPayload, aError: string): Boolean;
function IsJWTTokenValid(aConnection: TsgcWSConnection; aHeaders: TStringList): Boolean;
function IsJWTUnauthorized(aConnection: TsgcWSConnection): Boolean;
procedure GetJWTResponseError(const aConnection: TsgcWSConnection; var aResponseCode: Integer; var aResponseText: string; var aHeaders: TStringList);
```

C++Builder

```cpp
bool __fastcall Validate(const UnicodeString aJWT, UnicodeString &aHeader, UnicodeString &aPayload, UnicodeString &aError);
bool __fastcall IsJWTTokenValid(TsgcWSConnection * aConnection, TStringList * aHeaders);
bool __fastcall IsJWTUnauthorized(TsgcWSConnection * aConnection);
void __fastcall GetJWTResponseError(const TsgcWSConnection * aConnection, int &aResponseCode, UnicodeString &aResponseText, TStringList * &aHeaders);
```

