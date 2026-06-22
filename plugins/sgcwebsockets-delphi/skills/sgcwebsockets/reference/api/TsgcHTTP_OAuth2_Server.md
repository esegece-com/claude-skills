# TsgcHTTP_OAuth2_Server

unit: sgcHTTP
Edition: Enterprise

Add `sgcHTTP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OAuth2Options: TsgcHTTPOAuth2Server_Options` | [TsgcHTTPOAuth2Server_Options](../types/TsgcHTTPOAuth2Server_Options.md) | `__property TsgcHTTPOAuth2Server_Options * OAuth2Options;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `Apps: TsgcHTTPOAuthApps` | [TsgcHTTPOAuthApps](../types/TsgcHTTPOAuthApps.md) | `__property TsgcHTTPOAuthApps * Apps;` |
| `Providers: TsgcHTTPOAuthProviders` | [TsgcHTTPOAuthProviders](../types/TsgcHTTPOAuthProviders.md) | `__property TsgcHTTPOAuthProviders * Providers;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnOAuth2BeforeRequest: TsgcHTTPOAuth2BeforeRequestEvent` | [TsgcHTTPOAuth2BeforeRequestEvent](../types/TsgcHTTPOAuth2BeforeRequestEvent.md) | `__property TsgcHTTPOAuth2BeforeRequestEvent OnOAuth2BeforeRequest;` |
| `OnOAuth2BeforeDispatchPage: TsgcHTTPOAuth2BeforeDispatchPageEvent` | [TsgcHTTPOAuth2BeforeDispatchPageEvent](../types/TsgcHTTPOAuth2BeforeDispatchPageEvent.md) | `__property TsgcHTTPOAuth2BeforeDispatchPageEvent OnOAuth2BeforeDispatchPage;` |
| `OnOAuth2Authentication: TsgcHTTPOAuth2AuthenticationEvent` | [TsgcHTTPOAuth2AuthenticationEvent](../types/TsgcHTTPOAuth2AuthenticationEvent.md) | `__property TsgcHTTPOAuth2AuthenticationEvent OnOAuth2Authentication;` |
| `OnOAuth2AfterAccessToken: TsgcHTTPOAuth2AfterAccessTokenEvent` | [TsgcHTTPOAuth2AfterAccessTokenEvent](../types/TsgcHTTPOAuth2AfterAccessTokenEvent.md) | `__property TsgcHTTPOAuth2AfterAccessTokenEvent OnOAuth2AfterAccessToken;` |
| `OnOAuth2AfterRefreshToken: TsgcHTTPOAuth2AfterRefreshTokenEvent` | [TsgcHTTPOAuth2AfterRefreshTokenEvent](../types/TsgcHTTPOAuth2AfterRefreshTokenEvent.md) | `__property TsgcHTTPOAuth2AfterRefreshTokenEvent OnOAuth2AfterRefreshToken;` |
| `OnOAuth2AfterValidateAccessToken: TsgcHTTPOAuth2AfterValidateAccessTokenEvent` | [TsgcHTTPOAuth2AfterValidateAccessTokenEvent](../types/TsgcHTTPOAuth2AfterValidateAccessTokenEvent.md) | `__property TsgcHTTPOAuth2AfterValidateAccessTokenEvent OnOAuth2AfterValidateAccessToken;` |
| `OnOAuth2Unauthorized: TsgcHTTPOAuth2UnauthorizedEvent` | [TsgcHTTPOAuth2UnauthorizedEvent](../types/TsgcHTTPOAuth2UnauthorizedEvent.md) | `__property TsgcHTTPOAuth2UnauthorizedEvent OnOAuth2Unauthorized;` |
| `OnOAuth2ResponseError: TsgcHTTPOAuth2ResponseErrorEvent` | [TsgcHTTPOAuth2ResponseErrorEvent](../types/TsgcHTTPOAuth2ResponseErrorEvent.md) | `__property TsgcHTTPOAuth2ResponseErrorEvent OnOAuth2ResponseError;` |
| `OnOAuth2AfterRevokeToken: TsgcHTTPOAuth2AfterRevokeTokenEvent` | [TsgcHTTPOAuth2AfterRevokeTokenEvent](../types/TsgcHTTPOAuth2AfterRevokeTokenEvent.md) | `__property TsgcHTTPOAuth2AfterRevokeTokenEvent OnOAuth2AfterRevokeToken;` |
| `OnOAuth2AfterIntrospectToken: TsgcHTTPOAuth2AfterIntrospectTokenEvent` | [TsgcHTTPOAuth2AfterIntrospectTokenEvent](../types/TsgcHTTPOAuth2AfterIntrospectTokenEvent.md) | `__property TsgcHTTPOAuth2AfterIntrospectTokenEvent OnOAuth2AfterIntrospectToken;` |
| `OnOAuth2DeviceAuthorization: TsgcHTTPOAuth2DeviceAuthorizationEvent` | [TsgcHTTPOAuth2DeviceAuthorizationEvent](../types/TsgcHTTPOAuth2DeviceAuthorizationEvent.md) | `__property TsgcHTTPOAuth2DeviceAuthorizationEvent OnOAuth2DeviceAuthorization;` |
| `OnOAuth2DeviceCodeVerification: TsgcHTTPOAuth2DeviceCodeVerificationEvent` | [TsgcHTTPOAuth2DeviceCodeVerificationEvent](../types/TsgcHTTPOAuth2DeviceCodeVerificationEvent.md) | `__property TsgcHTTPOAuth2DeviceCodeVerificationEvent OnOAuth2DeviceCodeVerification;` |
| `OnOAuth2ValidateDPoP: TsgcHTTPOAuth2ValidateDPoPEvent` | [TsgcHTTPOAuth2ValidateDPoPEvent](../types/TsgcHTTPOAuth2ValidateDPoPEvent.md) | `__property TsgcHTTPOAuth2ValidateDPoPEvent OnOAuth2ValidateDPoP;` |

## Methods

Delphi

```pascal
function AddToken(const aAppName, aToken: string; aExpires: TDateTime; const aRefreshToken: string; const aScope: string = ''): Boolean;
function RemoveToken(const aToken: string): Boolean;
function RemoveTokenByRefreshToken(const aRefreshToken: string): Boolean;
function DoProcessHTTP(const aConnection: TsgcWSConnection; const aHeaders: TStringList): Boolean;
function IsOAuth2TokenValid(const aConnection: TsgcWSConnection; const aHeaders: TStringList): Boolean;
function IsOAuth2Unauthorized(aConnection: TsgcWSConnection): Boolean;
procedure GetOAuth2ResponseError(const aConnection: TsgcWSConnection; var aResponseCode: Integer; var aResponseText: string; var aHeaders: TStringList);
function RegisterApp(const aName, aRedirectURI: String; var ClientId, ClientSecret: string): Boolean;
function UnRegisterApp(const aName: string): Boolean;
function GetApp(const aName: string): TsgcHTTPOAuthApp;
function GetAppByClientId(const aClientId: string): TsgcHTTPOAuthApp;
function RegisterProvider(const aName, aClientId, aClientSecret, aAuthorizeURL, aTokenURL, aScope, aURL, aCallbackURL: string): Boolean;
function UnRegisterProvider(const aName: string): Boolean;
function GetProviderByLoginRequest(const aHeaders: TStringList) : TsgcHTTPOAuthProvider;
function GetProviderByCallbackRequest(const aHeaders: TStringList) : TsgcHTTPOAuthProvider;
procedure ClearProviders;
```

C++Builder

```cpp
bool __fastcall AddToken(const UnicodeString aAppName, const UnicodeString aToken, System::TDateTime aExpires, const UnicodeString aRefreshToken, const UnicodeString aScope = '');
bool __fastcall RemoveToken(const UnicodeString aToken);
bool __fastcall RemoveTokenByRefreshToken(const UnicodeString aRefreshToken);
bool __fastcall DoProcessHTTP(const TsgcWSConnection * aConnection, const TStringList * aHeaders);
bool __fastcall IsOAuth2TokenValid(const TsgcWSConnection * aConnection, const TStringList * aHeaders);
bool __fastcall IsOAuth2Unauthorized(TsgcWSConnection * aConnection);
void __fastcall GetOAuth2ResponseError(const TsgcWSConnection * aConnection, int &aResponseCode, UnicodeString &aResponseText, TStringList * &aHeaders);
bool __fastcall RegisterApp(const UnicodeString aName, const UnicodeString aRedirectURI, UnicodeString &ClientId, UnicodeString &ClientSecret);
bool __fastcall UnRegisterApp(const UnicodeString aName);
TsgcHTTPOAuthApp * __fastcall GetApp(const UnicodeString aName);
TsgcHTTPOAuthApp * __fastcall GetAppByClientId(const UnicodeString aClientId);
bool __fastcall RegisterProvider(const UnicodeString aName, const UnicodeString aClientId, const UnicodeString aClientSecret, const UnicodeString aAuthorizeURL, const UnicodeString aTokenURL, const UnicodeString aScope, const UnicodeString aURL, const UnicodeString aCallbackURL);
bool __fastcall UnRegisterProvider(const UnicodeString aName);
TsgcHTTPOAuthProvider * __fastcall GetProviderByLoginRequest(const TStringList * aHeaders);
TsgcHTTPOAuthProvider * __fastcall GetProviderByCallbackRequest(const TStringList * aHeaders);
void __fastcall ClearProviders();
```

