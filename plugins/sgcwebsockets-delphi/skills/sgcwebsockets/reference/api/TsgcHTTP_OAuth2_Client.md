# TsgcHTTP_OAuth2_Client

unit: sgcHTTP
Edition: Standard

Add `sgcHTTP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `LocalServerOptions: TsgcHTTPOAuth_LocalServerOptions` | [TsgcHTTPOAuth_LocalServerOptions](../types/TsgcHTTPOAuth_LocalServerOptions.md) | `__property TsgcHTTPOAuth_LocalServerOptions * LocalServerOptions;` |
| `AuthorizationServerOptions: TsgcHTTPOAuth_AuthorizationServer` | [TsgcHTTPOAuth_AuthorizationServer](../types/TsgcHTTPOAuth_AuthorizationServer.md) | `__property TsgcHTTPOAuth_AuthorizationServer * AuthorizationServerOptions;` |
| `OAuth2Options: TsgcHTTPOAuth2_Options` | [TsgcHTTPOAuth2_Options](../types/TsgcHTTPOAuth2_Options.md) | `__property TsgcHTTPOAuth2_Options * OAuth2Options;` |
| `HTTPClientOptions: TsgcHTTPClient_Options` | [TsgcHTTPClient_Options](../types/TsgcHTTPClient_Options.md) | `__property TsgcHTTPClient_Options * HTTPClientOptions;` |
| `DPoPOptions: TsgcHTTPOAuth2_DPoP_Options` | [TsgcHTTPOAuth2_DPoP_Options](../types/TsgcHTTPOAuth2_DPoP_Options.md) | `__property TsgcHTTPOAuth2_DPoP_Options * DPoPOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `AccessToken: String (read-only)` | `String` | `__property UnicodeString AccessToken /* read-only */;` |
| `TokenType: String (read-only)` | `String` | `__property UnicodeString TokenType /* read-only */;` |
| `CurrentExpiresIn: Integer (read-only)` | `Integer` | `__property int CurrentExpiresIn /* read-only */;` |
| `CurrentRefreshToken: String (read-only)` | `String` | `__property UnicodeString CurrentRefreshToken /* read-only */;` |
| `DPoPNonce: String (read-only)` | `String` | `__property UnicodeString DPoPNonce /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnBeforeAuthorizeCode: TsgcOnAuth2BeforeAuthorizeCode` | [TsgcOnAuth2BeforeAuthorizeCode](../types/TsgcOnAuth2BeforeAuthorizeCode.md) | `__property TsgcOnAuth2BeforeAuthorizeCode * OnBeforeAuthorizeCode;` |
| `OnAfterAuthorizeCode: TsgcOnAuth2AfterAuthorizeCode` | [TsgcOnAuth2AfterAuthorizeCode](../types/TsgcOnAuth2AfterAuthorizeCode.md) | `__property TsgcOnAuth2AfterAuthorizeCode * OnAfterAuthorizeCode;` |
| `OnErrorAuthorizeCode: TsgcOnAuth2ErrorAuthorizeCode` | [TsgcOnAuth2ErrorAuthorizeCode](../types/TsgcOnAuth2ErrorAuthorizeCode.md) | `__property TsgcOnAuth2ErrorAuthorizeCode * OnErrorAuthorizeCode;` |
| `OnBeforeAccessToken: TsgcOnAuth2BeforeAccessToken` | [TsgcOnAuth2BeforeAccessToken](../types/TsgcOnAuth2BeforeAccessToken.md) | `__property TsgcOnAuth2BeforeAccessToken * OnBeforeAccessToken;` |
| `OnAfterAccessToken: TsgcOnAuth2AfterAccessToken` | [TsgcOnAuth2AfterAccessToken](../types/TsgcOnAuth2AfterAccessToken.md) | `__property TsgcOnAuth2AfterAccessToken * OnAfterAccessToken;` |
| `OnErrorAccessToken: TsgcOnAuth2ErrorAccessToken` | [TsgcOnAuth2ErrorAccessToken](../types/TsgcOnAuth2ErrorAccessToken.md) | `__property TsgcOnAuth2ErrorAccessToken * OnErrorAccessToken;` |
| `OnBeforeRefreshToken: TsgcOnAuth2BeforeRefreshToken` | [TsgcOnAuth2BeforeRefreshToken](../types/TsgcOnAuth2BeforeRefreshToken.md) | `__property TsgcOnAuth2BeforeRefreshToken * OnBeforeRefreshToken;` |
| `OnAfterRefreshToken: TsgcOnAuth2AfterRefreshToken` | [TsgcOnAuth2AfterRefreshToken](../types/TsgcOnAuth2AfterRefreshToken.md) | `__property TsgcOnAuth2AfterRefreshToken * OnAfterRefreshToken;` |
| `OnErrorRefreshToken: TsgcOnAuth2ErrorRefreshToken` | [TsgcOnAuth2ErrorRefreshToken](../types/TsgcOnAuth2ErrorRefreshToken.md) | `__property TsgcOnAuth2ErrorRefreshToken * OnErrorRefreshToken;` |
| `OnHTTPResponse: TsgcOnAuth2HTTPResponse` | [TsgcOnAuth2HTTPResponse](../types/TsgcOnAuth2HTTPResponse.md) | `__property TsgcOnAuth2HTTPResponse * OnHTTPResponse;` |
| `OnBeforeRevokeToken: TsgcOnAuth2BeforeRevokeToken` | [TsgcOnAuth2BeforeRevokeToken](../types/TsgcOnAuth2BeforeRevokeToken.md) | `__property TsgcOnAuth2BeforeRevokeToken * OnBeforeRevokeToken;` |
| `OnAfterRevokeToken: TsgcOnAuth2AfterRevokeToken` | [TsgcOnAuth2AfterRevokeToken](../types/TsgcOnAuth2AfterRevokeToken.md) | `__property TsgcOnAuth2AfterRevokeToken * OnAfterRevokeToken;` |
| `OnErrorRevokeToken: TsgcOnAuth2ErrorRevokeToken` | [TsgcOnAuth2ErrorRevokeToken](../types/TsgcOnAuth2ErrorRevokeToken.md) | `__property TsgcOnAuth2ErrorRevokeToken * OnErrorRevokeToken;` |
| `OnBeforeIntrospectToken: TsgcOnAuth2BeforeIntrospectToken` | [TsgcOnAuth2BeforeIntrospectToken](../types/TsgcOnAuth2BeforeIntrospectToken.md) | `__property TsgcOnAuth2BeforeIntrospectToken * OnBeforeIntrospectToken;` |
| `OnAfterIntrospectToken: TsgcOnAuth2AfterIntrospectToken` | [TsgcOnAuth2AfterIntrospectToken](../types/TsgcOnAuth2AfterIntrospectToken.md) | `__property TsgcOnAuth2AfterIntrospectToken * OnAfterIntrospectToken;` |
| `OnErrorIntrospectToken: TsgcOnAuth2ErrorIntrospectToken` | [TsgcOnAuth2ErrorIntrospectToken](../types/TsgcOnAuth2ErrorIntrospectToken.md) | `__property TsgcOnAuth2ErrorIntrospectToken * OnErrorIntrospectToken;` |
| `OnDeviceCode: TsgcOnAuth2DeviceCode` | [TsgcOnAuth2DeviceCode](../types/TsgcOnAuth2DeviceCode.md) | `__property TsgcOnAuth2DeviceCode * OnDeviceCode;` |
| `OnDeviceCodeExpired: TsgcOnAuth2DeviceCodeExpired` | [TsgcOnAuth2DeviceCodeExpired](../types/TsgcOnAuth2DeviceCodeExpired.md) | `__property TsgcOnAuth2DeviceCodeExpired * OnDeviceCodeExpired;` |
| `OnDPoPSign: TsgcOnDPoPSignEvent` | [TsgcOnDPoPSignEvent](../types/TsgcOnDPoPSignEvent.md) | `__property TsgcOnDPoPSignEvent OnDPoPSign;` |
| `OnAuthToken: TsgcOnAuthToken` | [TsgcOnAuthToken](../types/TsgcOnAuthToken.md) | `__property TsgcOnAuthToken * OnAuthToken;` |
| `OnAuthTokenError: TsgcOnAuthTokenError` | [TsgcOnAuthTokenError](../types/TsgcOnAuthTokenError.md) | `__property TsgcOnAuthTokenError * OnAuthTokenError;` |

## Methods

Delphi

```pascal
procedure Start;
procedure Refresh(const aRefreshToken: String);
procedure Revoke(const aToken: String; const aTokenTypeHint: String = '');
procedure Introspect(const aToken: String; const aTokenTypeHint: String = '');
procedure Stop;
function GetDPoPProof(const aMethod, aURL, aAccessToken: String): String;
function GetDPoPJWKThumbprint: String;
procedure GenerateDPoPKeyPair;
function PublicKeyToJWK(const aPEM: String): String;
```

C++Builder

```cpp
void __fastcall Start();
void __fastcall Refresh(const UnicodeString aRefreshToken);
void __fastcall Revoke(const UnicodeString aToken, const UnicodeString aTokenTypeHint = '');
void __fastcall Introspect(const UnicodeString aToken, const UnicodeString aTokenTypeHint = '');
void __fastcall Stop();
UnicodeString __fastcall GetDPoPProof(const UnicodeString aMethod, const UnicodeString aURL, const UnicodeString aAccessToken);
UnicodeString __fastcall GetDPoPJWKThumbprint();
void __fastcall GenerateDPoPKeyPair();
UnicodeString __fastcall PublicKeyToJWK(const UnicodeString aPEM);
```

