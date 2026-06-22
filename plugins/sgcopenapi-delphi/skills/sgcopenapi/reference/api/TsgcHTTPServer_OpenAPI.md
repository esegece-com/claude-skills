# TsgcHTTPServer_OpenAPI

unit: sgcHTTPServer_OpenAPI

Add `sgcHTTPServer_OpenAPI` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `Active: Boolean` | `Boolean` | `__property bool Active;` |
| `Bindings: TIdSocketHandles` | [TIdSocketHandles](../types/TIdSocketHandles.md) | `__property TIdSocketHandles * Bindings;` |
| `Port: Integer` | `Integer` | `__property int Port;` |
| `OpenAPIOptions: TsgcOpenAPIServer_Options` | [TsgcOpenAPIServer_Options](../types/TsgcOpenAPIServer_Options.md) | `__property TsgcOpenAPIServer_Options * OpenAPIOptions;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnRequest: TsgcOpenAPIRequestEvent` | [TsgcOpenAPIRequestEvent](../types/TsgcOpenAPIRequestEvent.md) | `__property TsgcOpenAPIRequestEvent OnRequest;` |
| `OnBeforeRequest: TsgcOpenAPIBeforeRequestEvent` | [TsgcOpenAPIBeforeRequestEvent](../types/TsgcOpenAPIBeforeRequestEvent.md) | `__property TsgcOpenAPIBeforeRequestEvent OnBeforeRequest;` |
| `OnAfterRequest: TsgcOpenAPIAfterRequestEvent` | [TsgcOpenAPIAfterRequestEvent](../types/TsgcOpenAPIAfterRequestEvent.md) | `__property TsgcOpenAPIAfterRequestEvent OnAfterRequest;` |
| `OnValidationError: TsgcOpenAPIValidationErrorEvent` | [TsgcOpenAPIValidationErrorEvent](../types/TsgcOpenAPIValidationErrorEvent.md) | `__property TsgcOpenAPIValidationErrorEvent OnValidationError;` |
| `OnAuthenticate: TsgcOpenAPIAuthenticateEvent` | [TsgcOpenAPIAuthenticateEvent](../types/TsgcOpenAPIAuthenticateEvent.md) | `__property TsgcOpenAPIAuthenticateEvent OnAuthenticate;` |
| `OnException: TsgcOpenAPIExceptionEvent` | [TsgcOpenAPIExceptionEvent](../types/TsgcOpenAPIExceptionEvent.md) | `__property TsgcOpenAPIExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure LoadFromFile(const aFileName: string);
procedure LoadFromString(const aSpec: string);
```

C++Builder

```cpp
void __fastcall LoadFromFile(const UnicodeString aFileName);
void __fastcall LoadFromString(const UnicodeString aSpec);
```

