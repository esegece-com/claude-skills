# TsgcHTTPGoogleCloud_FCM_Client

unit: sgcHTTP
Edition: requires SGC_GOOGLE_CLOUD

Add `sgcHTTP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `GoogleCloudOptions: TsgcHTTP_Google_Cloud_Options` | [TsgcHTTP_Google_Cloud_Options](../types/TsgcHTTP_Google_Cloud_Options.md) | `__property TsgcHTTP_Google_Cloud_Options * GoogleCloudOptions;` |
| `LogFile: TsgcGoogleCloudLogFile` | [TsgcGoogleCloudLogFile](../types/TsgcGoogleCloudLogFile.md) | `__property TsgcGoogleCloudLogFile * LogFile;` |
| `TLSOptions: TsgcHTTPTLS_Options` | [TsgcHTTPTLS_Options](../types/TsgcHTTPTLS_Options.md) | `__property TsgcHTTPTLS_Options * TLSOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnAuthToken: TsgcOnAuthToken` | [TsgcOnAuthToken](../types/TsgcOnAuthToken.md) | `__property TsgcOnAuthToken * OnAuthToken;` |
| `OnAuthTokenError: TsgcOnAuthTokenError` | [TsgcOnAuthTokenError](../types/TsgcOnAuthTokenError.md) | `__property TsgcOnAuthTokenError * OnAuthTokenError;` |

## Methods

Delphi

```pascal
procedure LoadSettingsFromFile(const aFileName: String);
procedure Clear;
function RefreshToken(const aToken: string): boolean;
```

C++Builder

```cpp
void __fastcall LoadSettingsFromFile(const UnicodeString aFileName);
void __fastcall Clear();
bool __fastcall RefreshToken(const UnicodeString aToken);
```

