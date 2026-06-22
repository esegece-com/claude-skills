# TsgcWSAPIServer_OpenAPI

unit: sgcWebSocket_Server_API_OpenAPI
Edition: Enterprise

Add `sgcWebSocket_Server_API_OpenAPI` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OpenAPIOptions: TsgcOpenAPIServer_Options` | [TsgcOpenAPIServer_Options](../types/TsgcOpenAPIServer_Options.md) | `__property TsgcOpenAPIServer_Options * OpenAPIOptions;` |
| `Server: TsgcWSComponent_Server` | [TsgcWSComponent_Server](../types/TsgcWSComponent_Server.md) | `__property TsgcWSComponent_Server * Server;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnRequest: TsgcOpenAPIRequestEvent` | [TsgcOpenAPIRequestEvent](../types/TsgcOpenAPIRequestEvent.md) | `__property TsgcOpenAPIRequestEvent OnRequest;` |
| `OnBeforeRequest: TsgcOpenAPIBeforeRequestEvent` | [TsgcOpenAPIBeforeRequestEvent](../types/TsgcOpenAPIBeforeRequestEvent.md) | `__property TsgcOpenAPIBeforeRequestEvent OnBeforeRequest;` |
| `OnAfterRequest: TsgcOpenAPIAfterRequestEvent` | [TsgcOpenAPIAfterRequestEvent](../types/TsgcOpenAPIAfterRequestEvent.md) | `__property TsgcOpenAPIAfterRequestEvent OnAfterRequest;` |
| `OnValidationError: TsgcOpenAPIValidationErrorEvent` | [TsgcOpenAPIValidationErrorEvent](../types/TsgcOpenAPIValidationErrorEvent.md) | `__property TsgcOpenAPIValidationErrorEvent OnValidationError;` |
| `OnAuthenticate: TsgcOpenAPIAuthenticateEvent` | [TsgcOpenAPIAuthenticateEvent](../types/TsgcOpenAPIAuthenticateEvent.md) | `__property TsgcOpenAPIAuthenticateEvent OnAuthenticate;` |
| `OnException: TsgcOpenAPIExceptionEvent` | [TsgcOpenAPIExceptionEvent](../types/TsgcOpenAPIExceptionEvent.md) | `__property TsgcOpenAPIExceptionEvent OnException;` |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |

## Methods

Delphi

```pascal
procedure LoadFromFile(const aFileName: string);
procedure LoadFromString(const aSpec: string);
procedure KeepAlive(const aConnection: TsgcWSConnection; const aMessage: string);
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall LoadFromFile(const UnicodeString aFileName);
void __fastcall LoadFromString(const UnicodeString aSpec);
void __fastcall KeepAlive(const TsgcWSConnection * aConnection, const UnicodeString aMessage);
void __fastcall QueueClear();
```

