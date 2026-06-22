# TsgcHTTPGoogleCloud_Calendar_Client

unit: sgcHTTP
Edition: Standard

Add `sgcHTTP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `GoogleCloudOptions: TsgcHTTP_Google_Cloud_Options` | [TsgcHTTP_Google_Cloud_Options](../types/TsgcHTTP_Google_Cloud_Options.md) | `__property TsgcHTTP_Google_Cloud_Options * GoogleCloudOptions;` |
| `LogFile: TsgcAWSLogFile` | [TsgcAWSLogFile](../types/TsgcAWSLogFile.md) | `__property TsgcAWSLogFile * LogFile;` |
| `Scopes: TsgcGoogleCalendarScopes` | [TsgcGoogleCalendarScopes](../types/TsgcGoogleCalendarScopes.md) | `__property TsgcGoogleCalendarScopes * Scopes;` |
| `TLSOptions: TsgcHTTPTLS_Options` | [TsgcHTTPTLS_Options](../types/TsgcHTTPTLS_Options.md) | `__property TsgcHTTPTLS_Options * TLSOptions;` |
| `Version: string` | `string` | `__property UnicodeString Version;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnAuthToken: TsgcOnAuthToken` | [TsgcOnAuthToken](../types/TsgcOnAuthToken.md) | `__property TsgcOnAuthToken * OnAuthToken;` |
| `OnAuthTokenError: TsgcOnAuthTokenError` | [TsgcOnAuthTokenError](../types/TsgcOnAuthTokenError.md) | `__property TsgcOnAuthTokenError * OnAuthTokenError;` |
| `OnGetCalendar: TsgcGoogleCalendarEvent` | [TsgcGoogleCalendarEvent](../types/TsgcGoogleCalendarEvent.md) | `__property TsgcGoogleCalendarEvent OnGetCalendar;` |
| `OnGetCalendarEvent: TsgcGoogleCalendarGetEventEvent` | [TsgcGoogleCalendarGetEventEvent](../types/TsgcGoogleCalendarGetEventEvent.md) | `__property TsgcGoogleCalendarGetEventEvent OnGetCalendarEvent;` |
| `OnError: TsgcHTTP3ErrorEvent` | `TsgcHTTP3ErrorEvent` | `__property TsgcHTTP3ErrorEvent OnError;` |

