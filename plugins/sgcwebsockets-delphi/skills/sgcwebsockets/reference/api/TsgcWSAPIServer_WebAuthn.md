# TsgcWSAPIServer_WebAuthn

unit: sgcWebSocket_Server_APIs
Edition: Enterprise

Add `sgcWebSocket_Server_APIs` to your `uses` clause. Property and event types that link below are documented under `reference/types/`.

## Properties

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `WebAuthnOptions: TsgcWSWebAuthnServer_Options` | [TsgcWSWebAuthnServer_Options](../types/TsgcWSWebAuthnServer_Options.md) | `__property TsgcWSWebAuthnServer_Options * WebAuthnOptions;` |
| `EndpointsOptions: TsgcWSWebAuthnEndpoints_Options` | [TsgcWSWebAuthnEndpoints_Options](../types/TsgcWSWebAuthnEndpoints_Options.md) | `__property TsgcWSWebAuthnEndpoints_Options * EndpointsOptions;` |
| `Server: TsgcWSComponent_Server` | [TsgcWSComponent_Server](../types/TsgcWSComponent_Server.md) | `__property TsgcWSComponent_Server * Server;` |
| `Version: String (read-only)` | `String` | `__property UnicodeString Version /* read-only */;` |
| `RawMessages: Boolean` | `Boolean` | `__property bool RawMessages;` |
| `QueueMessages: Boolean` | `Boolean` | `__property bool QueueMessages;` |

## Events

| Delphi | Type | C++Builder |
| --- | --- | --- |
| `OnWebAuthnException: TsgcWebAuthnOnExceptionEvent` | [TsgcWebAuthnOnExceptionEvent](../types/TsgcWebAuthnOnExceptionEvent.md) | `__property TsgcWebAuthnOnExceptionEvent OnWebAuthnException;` |
| `OnWebAuthnHTTPRequest: TsgcWebAuthnOnHTTPRequest` | [TsgcWebAuthnOnHTTPRequest](../types/TsgcWebAuthnOnHTTPRequest.md) | `__property TsgcWebAuthnOnHTTPRequest * OnWebAuthnHTTPRequest;` |
| `OnWebAuthnHTTPResponse: TsgcWebAuthnOnHTTPResponse` | [TsgcWebAuthnOnHTTPResponse](../types/TsgcWebAuthnOnHTTPResponse.md) | `__property TsgcWebAuthnOnHTTPResponse * OnWebAuthnHTTPResponse;` |
| `OnWebAuthnRegistrationOptionsRequest: TsgcWebAuthnOnRegistrationOptionsRequest` | [TsgcWebAuthnOnRegistrationOptionsRequest](../types/TsgcWebAuthnOnRegistrationOptionsRequest.md) | `__property TsgcWebAuthnOnRegistrationOptionsRequest * OnWebAuthnRegistrationOptionsRequest;` |
| `OnWebAuthnRegistrationOptionsResponse: TsgcWebAuthnOnRegistrationOptionsResponse` | [TsgcWebAuthnOnRegistrationOptionsResponse](../types/TsgcWebAuthnOnRegistrationOptionsResponse.md) | `__property TsgcWebAuthnOnRegistrationOptionsResponse * OnWebAuthnRegistrationOptionsResponse;` |
| `OnWebAuthnRegistrationValidateCredentialId: TsgcWebAuthnOnRegistrationValidateCredentialId` | [TsgcWebAuthnOnRegistrationValidateCredentialId](../types/TsgcWebAuthnOnRegistrationValidateCredentialId.md) | `__property TsgcWebAuthnOnRegistrationValidateCredentialId * OnWebAuthnRegistrationValidateCredentialId;` |
| `OnWebAuthnRegistrationValidateCertificate: TsgcWebAuthnOnRegistrationValidateCertificate` | [TsgcWebAuthnOnRegistrationValidateCertificate](../types/TsgcWebAuthnOnRegistrationValidateCertificate.md) | `__property TsgcWebAuthnOnRegistrationValidateCertificate * OnWebAuthnRegistrationValidateCertificate;` |
| `OnWebAuthnRegistrationSuccessful: TsgcWebAuthnOnRegistrationSuccessful` | [TsgcWebAuthnOnRegistrationSuccessful](../types/TsgcWebAuthnOnRegistrationSuccessful.md) | `__property TsgcWebAuthnOnRegistrationSuccessful * OnWebAuthnRegistrationSuccessful;` |
| `OnWebAuthnRegistrationError: TsgcWebAuthnOnRegistrationError` | [TsgcWebAuthnOnRegistrationError](../types/TsgcWebAuthnOnRegistrationError.md) | `__property TsgcWebAuthnOnRegistrationError * OnWebAuthnRegistrationError;` |
| `OnWebAuthnAuthenticationOptionsRequest: TsgcWebAuthnOnAuthenticationOptionsRequest` | [TsgcWebAuthnOnAuthenticationOptionsRequest](../types/TsgcWebAuthnOnAuthenticationOptionsRequest.md) | `__property TsgcWebAuthnOnAuthenticationOptionsRequest * OnWebAuthnAuthenticationOptionsRequest;` |
| `OnWebAuthnAuthenticationOptionsResponse: TsgcWebAuthnOnAuthenticationOptionsResponse` | [TsgcWebAuthnOnAuthenticationOptionsResponse](../types/TsgcWebAuthnOnAuthenticationOptionsResponse.md) | `__property TsgcWebAuthnOnAuthenticationOptionsResponse * OnWebAuthnAuthenticationOptionsResponse;` |
| `OnWebAuthnAuthenticationSuccessful: TsgcWebAuthnOnAuthenticationSuccessful` | [TsgcWebAuthnOnAuthenticationSuccessful](../types/TsgcWebAuthnOnAuthenticationSuccessful.md) | `__property TsgcWebAuthnOnAuthenticationSuccessful * OnWebAuthnAuthenticationSuccessful;` |
| `OnWebAuthnAuthenticationError: TsgcWebAuthnOnAuthenticationError` | [TsgcWebAuthnOnAuthenticationError](../types/TsgcWebAuthnOnAuthenticationError.md) | `__property TsgcWebAuthnOnAuthenticationError * OnWebAuthnAuthenticationError;` |
| `OnWebAuthnMetadata: TsgcWebAuthnOnMetadata` | [TsgcWebAuthnOnMetadata](../types/TsgcWebAuthnOnMetadata.md) | `__property TsgcWebAuthnOnMetadata * OnWebAuthnMetadata;` |
| `OnWebAuthnUnauthorized: TsgcWebAuthnOnUnauthorizedEvent` | [TsgcWebAuthnOnUnauthorizedEvent](../types/TsgcWebAuthnOnUnauthorizedEvent.md) | `__property TsgcWebAuthnOnUnauthorizedEvent OnWebAuthnUnauthorized;` |
| `OnConnect: TsgcWSConnectEvent` | [TsgcWSConnectEvent](../types/TsgcWSConnectEvent.md) | `__property TsgcWSConnectEvent OnConnect;` |
| `OnDisconnect: TsgcWSDisconnectEvent` | [TsgcWSDisconnectEvent](../types/TsgcWSDisconnectEvent.md) | `__property TsgcWSDisconnectEvent OnDisconnect;` |
| `OnMessage: TsgcWSMessageEvent` | [TsgcWSMessageEvent](../types/TsgcWSMessageEvent.md) | `__property TsgcWSMessageEvent OnMessage;` |
| `OnBinary: TsgcWSBinaryEvent` | [TsgcWSBinaryEvent](../types/TsgcWSBinaryEvent.md) | `__property TsgcWSBinaryEvent OnBinary;` |
| `OnFragmented: TsgcWSFragmentedEvent` | [TsgcWSFragmentedEvent](../types/TsgcWSFragmentedEvent.md) | `__property TsgcWSFragmentedEvent OnFragmented;` |
| `OnError: TsgcWSErrorEvent` | [TsgcWSErrorEvent](../types/TsgcWSErrorEvent.md) | `__property TsgcWSErrorEvent OnError;` |
| `OnException: TsgcExceptionEvent` | [TsgcExceptionEvent](../types/TsgcExceptionEvent.md) | `__property TsgcExceptionEvent OnException;` |

## Methods

Delphi

```pascal
procedure AddCredential(const aCredential : TsgcWebAuthn_CredentialRecord);
function GetRegistrationOptionsResponse(const aPayload: string): string;
procedure ValidateRegistrationOptions(const aPayload: string);
function GetAuthenticationOptionsResponse(const aPayload: string): string;
procedure ValidateAuthenticationOptions(const aPayload: string);
procedure GetWebAuthnResponseError(const aConnection: TsgcWSConnection; var aResponseCode: Integer; var aResponseText: string; var aHeaders: TStringList);
function DoProcessHTTP(const aConnection: TsgcWSConnection; const aHeaders: TStringList): Boolean;
function IsWebAuthnRequest(const aHeaders: TStringList): Boolean;
function IsWebAuthnTokenValid(aConnection: TsgcWSConnection; aHeaders: TStringList): Boolean;
function IsWebAuthnUnauthorized(aConnection: TsgcWSConnection): Boolean;
procedure KeepAlive(const aConnection: TsgcWSConnection; const aMessage: string);
procedure QueueClear;
```

C++Builder

```cpp
void __fastcall AddCredential(const TsgcWebAuthn_CredentialRecord * aCredential);
UnicodeString __fastcall GetRegistrationOptionsResponse(const UnicodeString aPayload);
void __fastcall ValidateRegistrationOptions(const UnicodeString aPayload);
UnicodeString __fastcall GetAuthenticationOptionsResponse(const UnicodeString aPayload);
void __fastcall ValidateAuthenticationOptions(const UnicodeString aPayload);
void __fastcall GetWebAuthnResponseError(const TsgcWSConnection * aConnection, int &aResponseCode, UnicodeString &aResponseText, TStringList * &aHeaders);
bool __fastcall DoProcessHTTP(const TsgcWSConnection * aConnection, const TStringList * aHeaders);
bool __fastcall IsWebAuthnRequest(const TStringList * aHeaders);
bool __fastcall IsWebAuthnTokenValid(TsgcWSConnection * aConnection, TStringList * aHeaders);
bool __fastcall IsWebAuthnUnauthorized(TsgcWSConnection * aConnection);
void __fastcall KeepAlive(const TsgcWSConnection * aConnection, const UnicodeString aMessage);
void __fastcall QueueClear();
```

