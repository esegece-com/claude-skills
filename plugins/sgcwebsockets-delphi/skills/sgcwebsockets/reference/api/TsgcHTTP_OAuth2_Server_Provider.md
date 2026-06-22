# TsgcHTTP_OAuth2_Server_Provider

unit: sgcHTTP
Edition: requires SGC_OAUTH_SERVER

Add `sgcHTTP` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OAuth2Options: TsgcHTTPOAuth2_Options` | [TsgcHTTPOAuth2_Options](../types/TsgcHTTPOAuth2_Options.md) | `__property TsgcHTTPOAuth2_Options * OAuth2Options;` |
| `Version: string` | `string` | `__property UnicodeString Version;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnOAuth2BeforeRequest: TsgcHTTPOAuth2BeforeRequestEvent` | [TsgcHTTPOAuth2BeforeRequestEvent](../types/TsgcHTTPOAuth2BeforeRequestEvent.md) | `__property TsgcHTTPOAuth2BeforeRequestEvent OnOAuth2BeforeRequest;` |
| `OnOAuth2ProviderTokenValid: TsgcHTTPOAuth2ProviderTokenValidEvent` | [TsgcHTTPOAuth2ProviderTokenValidEvent](../types/TsgcHTTPOAuth2ProviderTokenValidEvent.md) | `__property TsgcHTTPOAuth2ProviderTokenValidEvent OnOAuth2ProviderTokenValid;` |
| `OnOAuth2ProviderTokenUnknown: TsgcHTTPOAuth2ProviderTokenUnknownEvent` | [TsgcHTTPOAuth2ProviderTokenUnknownEvent](../types/TsgcHTTPOAuth2ProviderTokenUnknownEvent.md) | `__property TsgcHTTPOAuth2ProviderTokenUnknownEvent OnOAuth2ProviderTokenUnknown;` |
| `OnOAuth2IsPrivateEndpoint: TsgcHTTPOAuth2IsPrivateEndpointEvent` | [TsgcHTTPOAuth2IsPrivateEndpointEvent](../types/TsgcHTTPOAuth2IsPrivateEndpointEvent.md) | `__property TsgcHTTPOAuth2IsPrivateEndpointEvent OnOAuth2IsPrivateEndpoint;` |

